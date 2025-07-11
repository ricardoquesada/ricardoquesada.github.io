---
author: ricardoquesada
category:
  - cocos2d
  - programming
date: "2014-04-23T21:51:26+00:00"
guid: http://towp8.com/?p=241
summary: |-
  LiquidFun Testbed + Cocos2d-x

  From LiquidFun's site:

  > Based on [Box2d](https://github.com/cocos2d/cocos2d-x-samples/blob/v3/box2d.org), [LiquidFun](http://google.github.io/liquidfun/) features particle-based fluid simulation. Game developers can use it for new game mechanics and add realistic physics to game play. Designers can use the library to create beautiful fluid interactive experiences.

  Basically LiquidFun is Box2d plus an extension to simulate fluids using a particle system. To test it, download and install the official [LiquidFun - Testbed,](https://play.google.com/store/apps/details?id=com.wolff.liquidfun.testbed2) and [LiquidFun - EyeCandy](https://play.google.com/store/apps/details?id=com.wolff.EyeCandy) for Android.

  [Cocos2d-x](http://cocos2d-x.org) already has Box2d integration, so in order to integrate Cocos2d-x with LiquidFun, we only need to integrate this new class: `b2ParticleSystem`.

  ### LiquidFun's b2ParticleSystem

  I'm not going to describe how to use LiquidFun (for that, read [its programmers guide](http://google.github.io/liquidfun/Programmers-Guide/html/index.html)). Instead, I'm going to describe how to integrate `b2ParticleSystem` in Cocos2d-x (also applicable to any other game engine).

  For the integration, what we need is a Cocos2d-x node that knows how to render a `b2ParticleSystem`. And [b2ParticleSystem](https://github.com/google/liquidfun/blob/v1.0.0/liquidfun/Box2D/Box2D/Particle/b2ParticleSystem.h#L189) has these 4 useful methods:

  Ideally we should be able to reuse `cocos2d::ParticleSystemQuad` for the rendering, but we can't because:

  - `cocos2d::ParticleSystemQuad` doesn't support changing the attractor (this is a design bug, we need to fix it). A _nil_ attractor would be needed for this case.
  - `ParticleSystemQuad` works with Quads, and not Points. And even if Points were supported (like in Cocos2d-x v1), it wouldn't work because the points and colors should be in an interleaved array.
  - The other issue is the conversion between Box2d and Cocos2d-x coordinate system, but it would be easy to fix.
tag:
  - cocos2d-x
  - liquidfun
title: 'Integrating LiquidFun with Cocos2d-x: Part I'
url: /2014/04/23/integrating-liquidfun-with-cocos2d-x-part-i/

---
![LiquidFun Testbed + Cocos2d-x](https://camo.githubusercontent.com/024bc94a0b655472808a1073611f72bff59f3f50/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f2d64705a666f5a3776472d512f553153304746486d6879492f41414141414141413735492f574b6e764e7334597069382f733430302f494d475f303031322e6a7067)

*LiquidFun Testbed + Cocos2d-x*

From LiquidFun's site:

> Based on [Box2d](https://github.com/cocos2d/cocos2d-x-samples/blob/v3/box2d.org), [LiquidFun](http://google.github.io/liquidfun/) features particle-based fluid simulation. Game developers can use it for new game mechanics and add realistic physics to game play. Designers can use the library to create beautiful fluid interactive experiences.

Basically LiquidFun is Box2d plus an extension to simulate fluids using a particle system. To test it, download and install the official [LiquidFun - Testbed,](https://play.google.com/store/apps/details?id=com.wolff.liquidfun.testbed2) and [LiquidFun - EyeCandy](https://play.google.com/store/apps/details?id=com.wolff.EyeCandy) for Android.

[Cocos2d-x](http://cocos2d-x.org) already has Box2d integration, so in order to integrate Cocos2d-x with LiquidFun, we only need to integrate this new class: `b2ParticleSystem`.

### LiquidFun's b2ParticleSystem

I'm not going to describe how to use LiquidFun (for that, read [its programmers guide](http://google.github.io/liquidfun/Programmers-Guide/html/index.html)). Instead, I'm going to describe how to integrate `b2ParticleSystem` in Cocos2d-x (also applicable to any other game engine).

For the integration, what we need is a Cocos2d-x node that knows how to render a `b2ParticleSystem`. And [b2ParticleSystem](https://github.com/google/liquidfun/blob/v1.0.0/liquidfun/Box2D/Box2D/Particle/b2ParticleSystem.h#L189) has these 4 useful methods:

```cpp
class b2ParticleSystem {
 ...
 // Get the number of particles.
 int32 GetParticleCount() const;

 // Get the particle radius.
 float32 GetRadius() const;

 // Get the position of each particle in Box2d's coordinate system
 // Array is length GetParticleCount()
 b2Vec2* GetPositionBuffer();

 // Get the color of each particle in RGBA Uint8 format.
 // Array is length GetParticleCount()
 b2ParticleColor* GetColorBuffer();
};
```

Ideally we should be able to reuse `cocos2d::ParticleSystemQuad` for the rendering, but we can't because:

- `cocos2d::ParticleSystemQuad` doesn't support changing the attractor (this is a design bug, we need to fix it). A _nil_ attractor would be needed for this case.
- `ParticleSystemQuad` works with Quads, and not Points. And even if Points were supported (like in Cocos2d-x v1), it wouldn't work because the points and colors should be in an interleaved array.
- The other issue is the conversion between Box2d and Cocos2d-x coordinate system, but it would be easy to fix.

### Points vs. Quads

The major drawback of using Points (instead of Quads), is that you cannot rotate a Point (spinning). And that's why we are not using them on Cocos2d-x.

And the benefits of using Points (instead of Quads) are that less memory is required, and that means that it could be faster. As an example:

- Point uses one point for the position (instead of 4 for the quad)
- Point uses one color (instead of 4)
- Point doesn't need the UV coordinates (zero points instead of 4)
- But if you want to use different sizes, you need to pass an array of floats (not needed if you are using quads).
- And from LiquidFun's point of view, it is cheaper to do collision detection with circles (point + radius) than with quads

It is noteworthy that LiquidFun's goal is to simulate fluids. And since in fluids you don't need to spin the particles, LiquidFun uses Points (since they take less memory and they are faster).

### Drawing using `GL_POINTS`

In OpenGL / OpenGL ES you can draw points using `GL_POINTS`, but it has certain limitations:

- It is not possible to rotate them (already discussed)
- If you scale the particle (by using `gl_PointSize`), you cannot scale the X-axis independent from the Y-axis.
- Points can use textures as well, but you cannot change the u-v coordinates. Either you use the full texture, or nothing.

If you haven't used `GL_POINTS` before, this is how the code should look like:

```cpp
// Create the array of positions. They are in Box2d's coordinate system
// The will be converted later to cocos2d's coordinate system
void *positions = _particleSystem->GetPositionBuffer();
glVertexAttribPointer(position_index, 2, GL_FLOAT, GL_FALSE, 0, positions);
glEnableVertexAttribArray(position_index);

// Array of colors. Format is: R,G,B,A unsigned bytes
void *colors= _particleSystem->GetColorBuffer();
glVertexAttribPointer(color_index, 4, GL_UNSIGNED_BYTE, GL_TRUE, 0, colors);
glEnableVertexAttribArray(color_index);

// Array of sizes. particle_size is an array of floats. The user should create it.
// This is an optional feature in order to have different sizes for the particles.
glVertexAttribPointer(particlesize_index, 1, GL_FLOAT, GL_FALSE, 0, particle_size);
glEnableVertexAttribArray(particlesize_index);

// Draw them as points
glDrawArrays(GL_POINTS, 0, _particleSystem->GetParticleCount());
```

### Converting positions from Box2d to Cocos2d-x coordinate system

Cocos2d-x v3.0 passes the Model View matrix to the `draw()` method.  And what we need to do is to transform it so that we can use the Positions that are in Box2d's coordinate system. And this is what we should do:

```cpp
class LFParticleSystemNode : public cocos2d::Node {
 ...
 // ivar for the scaling transform
 kmMat4 _ratioTransform;
}

bool LFParticleSystemNode::init(b2ParticleSystem* particleSystem, float ratio)
{
 ...
 // Pixels to Meters ratio: converts Box2d into cocos2d
 kmMat4Scaling(&_ratioTransform, ratio, ratio, 1);
 ...
}

void LFParticleSystemNode::onDraw(const kmMat4 &modelViewTransform, bool transformUpdated)
{
 // A new model view will be used, which lets us render the particles in cocos2d coordinate system
 // newMV = modelViewTransform * _ratioTransform
 kmMat4 newMV;
 kmMat4Multiply(&newMV, &modelViewTransform, &_ratioTransform);
 _shaderProgram->use();
 _shaderProgram->setUniformsForBuiltins(newMV);
 ...
}
```

### Changing the size with `gl_PointSize`

Another thing that is missing is to scale up/down the Points according to the "world" scale. And this is how we do it:

```cpp
// Vertex Shader
attribute vec4 a_position;
attribute vec4 a_color;
attribute float a_size;

void main()
{
 // CC_PMatrix = Projection Matrix
 // CC_MVMatrix = ModelView Matrix
 gl_Position = CC_PMatrix * CC_MVMatrix * a_position;

 // This is the trick to scale up/down the points:
 // The ModelView matrix has the ScaleX value in [0][0], and ScaleY value in [1][1]
 // Unfortunately we can only use either ScaleX or ScaleY, but not both.
 gl_PointSize = CC_MVMatrix[0][0] * a_size;
 v_fragmentColor = a_color;
}
```

### Texture Coordiantes with `gl_PointCoord`

The final thing to do, is use a texture for the particles, otherwise we will see a square. As I mentioned before, you cannot pass u-v coordinates for `GL_POINTS`. Instead, we are going to use the predefined variable called `gl_PointCoord`. Example:

```cpp
// Fragment Shader
uniform sampler2D CC_Texture0;

varying vec4 v_fragmentColor;
void main()
{
 // gl_PointCoord has the current "pixel" for the fragment
 // It uses the full texture. We can't use a "subrect" for this.
 gl_FragColor = v_fragmentColor * texture2D(CC_Texture0, gl_PointCoord);
}
```

And that's all!

The complete `LFParticleSystemNode` code can be found here:

- [LFParticleSystemNode.cpp](https://github.com/cocos2d/cocos2d-x-samples/blob/v3/samples/LiquidFun-EyeCandy/Classes/LFParticleSystemNode.cpp)

And the full working example can be downloaded from here:

- [cocos2d-x-samples](https://github.com/cocos2d/cocos2d-x-samples): Try both LiquidFun-EyeCandy and LiquidFun-Testbed samples.

In Part II, I'll describe the steps needed to integrate LiquidFun with cocos2d-x for Win32 + Visual Studio. Later I'll describe how to use a nice "metaball / blob" shader to simulate water.

**Update:** [Part II is here](http://towp8.com/2014/07/30/integrating-liquidfun-with-cocos2d-x-part-ii/)

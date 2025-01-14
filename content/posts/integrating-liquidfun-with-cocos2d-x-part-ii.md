---
author: ricardoquesada
category:
  - cocos2d
  - programming
date: "2014-07-30T20:45:00+00:00"
guid: http://towp8.com/?p=477
summary: "In [Part I](//towp8.com/2014/04/23/integrating-liquidfun-with-cocos2d-x-part-i/) I described to how integrated LiquidFun with Cocos2d-x.\nIn this part (part II) I'll describe how to render the particles using a basic water effect.\n\n \n\nPart I uses just one `glDrawArrays(GL_POINTS, 0, total);` to draw the particles. And although that works to draw \"particles\", it is not enough to draw \"water\".\n\nDrawing \"water\" requires a more complex rendering algorithm, like the one used in this [example](http://www.patrickmatte.com/stuff/physicsLiquid/). And implementing an algorithm similar that one is what this article describes.\n\nThe algorithm works more or less like this:\n\n- Choose a white circle and blur it.\n  - You can blur the circle at runtime\n  - Or you can blur it off-line.\n- Create an a new frame-buffer (think of a clean off-screen buffer where you can render whatever you want)\n- Render the particles into the newly created frame-buffer using the blurred circle\n- Now render the frame-buffer into the main color-buffer using a threshold. The threshold could be something like this:\n  - If pixel.r < 0.1, discard the pixel (the pixel won't be drawn)\n  - If pixel.r < 0.2, draw a blue pixel (for the border, although this is optional)\n  - else draw a white pixel (the inner part of the water)\n\n### How to do it using Cocos2d-x and LiquidFun\n\nLet's take the [`LFParticleSystemNode`](https://github.com/cocos2d/cocos2d-x-samples/blob/v3.1/samples/LiquidFun-EyeCandy/Classes/LFParticleSystemNode.cpp) from Part I, and \"evolve\" it:\n\nThe first thing to do is to add the \"off-screen\" frame-buffer into the `LFParticleSystemNode` class. In Cocos2d-x, the \"off-screen\" buffers are created with the `RenderTexture` class. Example:\n\n\\[code language=\"cpp\"\\]\nbool LFParticleSystemNode::init(b2ParticleSystem\\* particleSystem, float ratio)\n{\n...\n // create an off-screen frame-buffer with the size of the screen\n auto s = Director::getInstance()->getWinSize();\n \\_renderTexture = cocos2d::RenderTexture::create(s.width, s.height, Texture2D::PixelFormat::RGBA8888);\n this->addChild(\\_renderTexture);\n \\_renderTexture->setAnchorPoint(Point::ANCHOR\\_MIDDLE);\n \\_renderTexture->setPosition(Point(s.width/2, s.height/2));\n\n // Change the default shader. Use a the threshold shader\n auto program = GLProgram::createWithByteArrays(\\_renderTextureShaderVert, \\_renderTextureShaderFrag);\n auto programState = GLProgramState::getOrCreateWithGLProgram(program);\n programState->setUniformFloat(\"u\\_threshold\\_discard\", 0.15);\n programState->setUniformFloat(\"u\\_threshold\\_border\", 0.3);\n\n...\n}\n\\[/code\\]\n\nAnd, as mentioned earlier, the `RenderTexture` (the off-screen frame-buffer) needs a shader with a threshold. The threshold shader should look like the following:\n\n\\[code language=\"cpp\"\\]\nvarying vec4 v\\_fragmentColor;\nvarying vec2 v\\_texCoord;\nuniform float u\\_threshold\\_discard;\nuniform float u\\_threshold\\_border;\n\nvoid main()\n{\n vec4 color = v\\_fragmentColor \\* texture2D(CC\\_Texture0, v\\_texCoord);\n if( color.r < u\\_threshold\\_discard)\n // black or discard\n color = vec4(0,0,0,0);\n else if( color.r < u\\_threshold\\_border)\n // blue for the border\n color = vec4(0.2,0.2,0.9,1);\n else\n // white for the center\n color = vec4(1,1,1,1);\n gl\\_FragColor = color;\n}\n\\[/code\\]\n\nThe values `u_threshold_discard`, and `u_threshold_border` are defined at runtime. In the example, they are set at 0.15 and 0.3 respectively.\n\nThe next thing to do is, to render the particles in the `RenderTexture`.\n\n\\[code language=\"cpp\"\\]void LFParticleSystemNode::draw(Renderer \\*renderer, const Mat4 &transform, uint32\\_t transformFlags)\n{\n // tell RenderTexture to \"capture\" the particles\n    \\_renderTexture->beginWithClear(0,0,0,0);\n\n    \\_customCommand.init(\\_globalZOrder);\n    \\_customCommand.func = CC\\_CALLBACK\\_0(LFParticleSystemNode::onDraw, this, transform, transformFlags);\n    renderer->addCommand(&\\_customCommand);\n\n // tell RenderTexture to stop \"capturing\" the particles\n    \\_renderTexture->end();\n}\n\\[/code\\]\n\n### The result is the following"
tag:
  - cocos2d-x
  - liquidfun
title: 'Integrating LiquidFun with Cocos2d-x: Part II'
url: /2014/07/30/integrating-liquidfun-with-cocos2d-x-part-ii/

---
In [Part I](//towp8.com/2014/04/23/integrating-liquidfun-with-cocos2d-x-part-i/) I described to how integrated LiquidFun with Cocos2d-x.
In this part (part II) I'll describe how to render the particles using a basic water effect.

{{< figure align=alignnone width=425 src="/wp-content/uploads/2014/07/screenshot-2014-07-29-19-02-07.png?w=676" alt="" >}}

Part I uses just one `glDrawArrays(GL_POINTS, 0, total);` to draw the particles. And although that works to draw "particles", it is not enough to draw "water".

Drawing "water" requires a more complex rendering algorithm, like the one used in this [example](http://www.patrickmatte.com/stuff/physicsLiquid/). And implementing an algorithm similar that one is what this article describes.

The algorithm works more or less like this:

- Choose a white circle and blur it.
  - You can blur the circle at runtime
  - Or you can blur it off-line.
- Create an a new frame-buffer (think of a clean off-screen buffer where you can render whatever you want)
- Render the particles into the newly created frame-buffer using the blurred circle
- Now render the frame-buffer into the main color-buffer using a threshold. The threshold could be something like this:
  - If pixel.r < 0.1, discard the pixel (the pixel won't be drawn)
  - If pixel.r < 0.2, draw a blue pixel (for the border, although this is optional)
  - else draw a white pixel (the inner part of the water)

### How to do it using Cocos2d-x and LiquidFun

Let's take the [`LFParticleSystemNode`](https://github.com/cocos2d/cocos2d-x-samples/blob/v3.1/samples/LiquidFun-EyeCandy/Classes/LFParticleSystemNode.cpp) from Part I, and "evolve" it:

The first thing to do is to add the "off-screen" frame-buffer into the `LFParticleSystemNode` class. In Cocos2d-x, the "off-screen" buffers are created with the `RenderTexture` class. Example:

\[code language="cpp"\]
bool LFParticleSystemNode::init(b2ParticleSystem\* particleSystem, float ratio)
{
...
 // create an off-screen frame-buffer with the size of the screen
 auto s = Director::getInstance()->getWinSize();
 \_renderTexture = cocos2d::RenderTexture::create(s.width, s.height, Texture2D::PixelFormat::RGBA8888);
 this->addChild(\_renderTexture);
 \_renderTexture->setAnchorPoint(Point::ANCHOR\_MIDDLE);
 \_renderTexture->setPosition(Point(s.width/2, s.height/2));

 // Change the default shader. Use a the threshold shader
 auto program = GLProgram::createWithByteArrays(\_renderTextureShaderVert, \_renderTextureShaderFrag);
 auto programState = GLProgramState::getOrCreateWithGLProgram(program);
 programState->setUniformFloat("u\_threshold\_discard", 0.15);
 programState->setUniformFloat("u\_threshold\_border", 0.3);

...
}
\[/code\]

And, as mentioned earlier, the `RenderTexture` (the off-screen frame-buffer) needs a shader with a threshold. The threshold shader should look like the following:

\[code language="cpp"\]
varying vec4 v\_fragmentColor;
varying vec2 v\_texCoord;
uniform float u\_threshold\_discard;
uniform float u\_threshold\_border;

void main()
{
 vec4 color = v\_fragmentColor \* texture2D(CC\_Texture0, v\_texCoord);
 if( color.r < u\_threshold\_discard)
 // black or discard
 color = vec4(0,0,0,0);
 else if( color.r < u\_threshold\_border)
 // blue for the border
 color = vec4(0.2,0.2,0.9,1);
 else
 // white for the center
 color = vec4(1,1,1,1);
 gl\_FragColor = color;
}
\[/code\]

The values `u_threshold_discard`, and `u_threshold_border` are defined at runtime. In the example, they are set at 0.15 and 0.3 respectively.

The next thing to do is, to render the particles in the `RenderTexture`.

\[code language="cpp"\]void LFParticleSystemNode::draw(Renderer \*renderer, const Mat4 &transform, uint32\_t transformFlags)
{
 // tell RenderTexture to "capture" the particles
    \_renderTexture->beginWithClear(0,0,0,0);

    \_customCommand.init(\_globalZOrder);
    \_customCommand.func = CC\_CALLBACK\_0(LFParticleSystemNode::onDraw, this, transform, transformFlags);
    renderer->addCommand(&\_customCommand);

 // tell RenderTexture to stop "capturing" the particles
    \_renderTexture->end();
}
\[/code\]

### The result is the following

{{< figure align=alignnone width=628 src="/wp-content/uploads/2014/07/part1%5Fpart2.jpg?w=676" alt="" >}}

### Further improvements

What I described is just a simple algorithm to render water. But more advanced (and better looking) algorithms could be implemented using the same principle:

- Render blurred (or any other effect) particles into an off-screen buffer
- Render the off-screen buffer with an special shader

As an example, the official ["LiquidFun - EyeCandy"](https://github.com/google/liquidfun/tree/master/liquidfun/Box2D/EyeCandy) sample  from Google uses a much more complex shader that involves lighting, refraction, and distortion in the background.

### Customizing shaders in Cocos2d-x v3.1+

Cocos2d-x v3.1 introduced a new way to customize shaders. The same `GLProgram` works like in v3.0, but if you want to add custom attributes or uniforms, instead of subclassing `GLProgram`, you can can do it by using the `GLProgramState` class. Subclassing `GLProgram` still works, but the recommend way is to use `GLProgramState`. It works like this:

\[code language="cpp"\]
// you create a GLProgram like in v3.0
GLProgram\* glprogram = GLProgram::createWithByteArrays(\_particleShaderVert, \_particleShaderFrag);

// and then you create a GLProgramState with it
GLProgramState\* glprogramstate = GLProgramState::getOrCreateWithGLProgram(glprogram);

// attach the ProgramState to a Node
sprite->setGLProgramState( glprogramstate );
\[/code\]

The next thing to do is to add custom uniforms and/or attributes using the [GLProgramState](https://github.com/cocos2d/cocos2d-x/blob/cocos2d-x-3.2/cocos/renderer/CCGLProgramState.h) API.

Adding custom uniforms:

\[code language="cpp"\]
// setting a float
glprogramstate->setUniformFloat("u\_name\_1", 0.15f);

// setting a vec2
glprogramstate->setUniformVec2("u\_name\_2", Vec2(0.2, 0.3));

// setting a callback
glprogramstate->setUniformCallback("uniform\_name\_2", \[\](GLProgram\* program, Uniform\* uniform){
 glUniform4fv( uniform->location, 10, \_buffer);
});
\[/code\]

And the same is true for attributes:

\[code language="cpp"\]
// setting an attribute pointer
glprogramstate->setVertexAttribPointer("a\_position", 2, GL\_FLOAT, GL\_FALSE, 0, \_particleSystem->GetPositionBuffer());

// setting a callback
glprogramstate->setVertexAttribCallback("a\_color", \[\](VertexAttrib\* vertexAttrib) {
 glVertexAttrib4f(vertexAttrib->index, 0.2, 0.8, 0.7, 1.0);
});
\[/code\]

### Download and running the sample

Clone the [cocos2d-x-samples](https://github.com/cocos2d/cocos2d-x-samples/) repo and follow its [instructions](https://github.com/cocos2d/cocos2d-x-samples/blob/v3/README.md). Then launch the "LiquidFun - EyeCandy" demo.

```
$ git clone https://github.com/cocos2d/cocos2d-x-samples.git
```

... and follow [instructions from the site](https://github.com/cocos2d/cocos2d-x-samples/blob/v3/README.md). And then launch it:

```
$ cd samples/LiquidFun-EyeCandy/proj.ios_mac
$ open LiquidFun-EyeCandy.xcodeproj
```

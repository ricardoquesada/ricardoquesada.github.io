# Ricardo Quesada's web page

Visit it at https://retro.moe or https://ricardoquesada.github.io

## Hugo Notes

### Update template

If template and Hugo are out of sync, it might trigger errors

```sh
cd ${SRC}/themes/PaperMod
git pull origin main
```

### Write a new blog post

1. Start Hugo server

    ```sh
    cd ${SRC}
    hugo build
    hugo server --buildDrafts
    ```

2. New blog post

   ```sh
   hugo new content content/posts/embroidery-angler-fish-blinking-led.md
   ```

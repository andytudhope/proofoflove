# Proof of Love

You, too, can build your own book, courtesy of the people at [Status](https://status.im) and some other friends. It's not perfect, but here's how you can get started today.

**Dependencies**

1. Try get a Linux machine. I haven't tested this anywhere else. Mac should work fine, but Windows might be a problem ([OS](https://www.youtube.com/watch?v=4vW62KqKJ5 "Revolution!") with [training wheels](https://github.com/andytudhope/APerspectiveonTechnologyA) that it is).
2. Download a good "code" editor. I use - wtih tongue in cheek after the OS video link - [VSCode](https://code.visualstudio.com/download); but Atom, Sublime, or even NoteBook++ will do, depending on if you already have a preference.
3. Once that is set up, install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
4. Then install Node and NPM (the Node Package Manager). The easiest way to do this, imo, is through [nvm](https://github.com/nvm-sh/nvm).

**Get going**

1. Make a new directory, using the name for your book. Open a terminal - `ctrl + alt + t` on [Ubuntu](https://www.ubuntu.com/download/desktop) - and run:

```bash
mkdir my-book-name
```

2. Clone the template repository and switch into the directory once created. In your same terminal, run:

```bash
git clone https://github.com/andytudhope/proofoflove.git my-book-name && cd my-book-name/
```

3. Install the required packages to build and run the site. Make sure you are in the root directory of the project and, in your terminal, run:

````bash
npm i
````

4. Build and start the site to see what you're dealing with. This is a three step process:
    1. from the same place, run 
    ```bash
    ./node_modules/.bin/gulp build
    ```
    2. _Open a new terminal while gulp watches for file changes and live reloads for you_
    3. Now run 
    ```bash
    cd my-book-name/ # Just to make sure your new session is in the correct place
    ./node_modules/.bin/hexo serve
    ```

With just four global dependencies, and four quick steps, we have a template for an online book! While I appreciate that this process is nowhere near as smooth as a professional platform like Gitbook, I still think that's pretty cool.

## How to Edit Stuff - a 12 Step Program

Now that you have the site up and running, you'll need to know where to go to change, add, and edit things.

1. If you installed VSCode, then, from the project root in your terminal, simply run:

```bash
code .
```

This will open the code editor with your project loaded into it's sidebar and allow you to see it visually, rather than just in a terminal.

2. Go to the `source` [folder](./source/) - this is where you will put all of your chapters, sections and content. You can create as many chapters (folders) as you like, and put as many files beneath each chapter as you like, each of which will appear in it's own place on the sidebar.

3. The sidebar will expand for the content beneath each specific chapter. So, if you go to [Canto I](https://thebluebook.co.za/canto-i/), for instance, you'll see that only the files beneath the `canto-i` [folder](https://github.com/andytudhope/thebluebook/tree/book/source/canto-i/) appear, and the rest of the Cantos are flattened. This is for easier navigation, and becomes even more important on mobile.

4. To control sidebar content, you need to adjust 2 files: 
    1. `source/_data/sidebar.yml`, which is where you control what each link resolves to, and 
    2. `themes/navy/languages/en.yml`, which is where you control the text that is shown to the reader. 
    Follow the patterns set up in those 2 files already and you should be fine.

5. One note about that `languages` folder - it can be used to handle translations quite elegantly, check out the [Hexo](https://hexo.io/docs/internationalization) docs for more on that.

6. Speaking of Hexo, the framework beneath this site, you'll need to edit the information in the `_config.yml` file in the root of the project to reflect your own book. A guide to doing this can be found [here](https://hexo.io/docs/configuration), but I suggest you stick as closely to the pattern already in that file as possible to avoid weird errors which I won't be able to help you fix. 

7. Oh, there are also [some great plugins and tricks](https://hexo.io/docs/tag-plugins) that come with Hexo by default to help you enrich your MD files with everything from quotes to images, videos and more.

8. If you want to add images, do it in `themes/navy/source/img` - the gulp build pipeline will put them in the right place so that you can simply link to them like [this](https://github.com/andytudhope/thebluebook/tree/book/source/fugue-i/index.md#L130).

9. If you want to change the page layout, or the home page, or the header and footer and other common elements, then you'll need to adventure into the `themes/navy/layout` folder, where you will find the few extended javascript `.ejs` files used to stitch it all together. Don't stress! This is just plain old HTML with a few fancy tags added to it to make fun things happen. If, for instance, you want to change the title of one the header items, all you need to do is go to this line in [themes/navy/layout/partial/header.js](./tree/master/themes/navy/layout/partial/header.js#) and edit the text there. You can just leave the rest of it as is, or explore the patterns to build your own, unique navigation elements.

10. If you want to change the styles, then you'll need to edit the CSS in `themes/navy/source/scss/main.scss`. I have tried to keep it as clean as possible, and suggest using the marked section at the bottom to insert your own styles so that you don't inadvertently break anything (or, more accurately, can find the problem easily when you do).

11. The same goes for editing the JS in `themes/navy/source/js/dev.js`. Note that work shoul happen in the `dev.js` file, as that is how [build pipline](./tree/master/gulpfile.js) is set up. I think it's awesome if you can, and it would be great to see developer-writers take this much further than I currently have.

12. When you're ready, you'll need to create your own respository. Do this through Github in your browser, then return to the root of your project, and run the following commands:

```bash
cd my-book-name/
git remote remove origin
git remote add origin https://github.com/<your_username>/<your_repo_name>.git
git add .
git commit -m "Initial setup done"
git push -u origin master
```
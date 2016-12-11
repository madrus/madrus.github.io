# Creating my blog with Jekyll on GitHub Pages

> Blog link: [https://madrus.github.io/][1]

For my theme, I have taken the [Lanyon Theme][2]. And here is its [source code link][3]. I have also found a very nice tutorial how to begin with it:  [GitHub Pages and Jekyll Beginner Video][4]. I have also decided to keep the original three posts of **Mark Otto** [@mdo](https://twitter.com/mdo) in my blog as an honor to his work and as an introduction to his theme.

## Prerequisites

In order to run the blog, we need **Ruby**, **Jekyll** and **Bundler**.

```bash
brew install ruby
sudo gem install jekyll
sudo gem install bundler
cd path/to/the/blog/directory
bundle install
```

## Initial Project Setup

* run the blog locally: `bundle exec jekyll serve`
* create a new `gh-pages` branch: `git branch gh-pages`
* push `master` and `gh-pages` branches to `GitHub`
* the blog will be available at [https://madrus.github.io/][1]
* If we want to our blog to be available at our own domain, we can add `CNAME` file in the root with just the `URL`, e.g.:

  ```text
  myblogurl.com
  ```

  As soon as we commit the file to the `gh-pages` repository and push it to `GitHub`, we can navigate to [myblogurl.com](http://myblogurl.com) to see our blog.

  * `git add .`
  * `git commit -am "cname added"`
  * `git push -u origin master`
  * `git checkout gh-pages`
  * `git merge master`
  * `git push -u origin gh-pages`

## Creating Markdown posts

This is work in progress.

## Enable Disqus comments

So far, I have followed the [Disqus instructions for Jekyll](https://madrus4u.disqus.com/admin/install/platforms/jekyll/) and added the [Universal Code](https://madrus4u.disqus.com/admin/install/platforms/universalcode/) to my two blog posts.

There are still questions:

1. Have I set up `indentifier` and `url` correctly?
2. How do I append `#disqus_thread` to the `href` attribute in my links?

## Sorting

* sort by blog post date descending:

  ```c
  {% assign posts_list = site.posts | sort: "url" | reverse %}
  ```

* sort categories alphabetically:

  ```c
  {% assign cats = site.categories | sort %}
  ```

## Links to contributors

We can `@mention` a GitHub username to generate a link to their profile. The resulting `<code><a></code>` element will link to the contributor's `GitHub Profile`. For example:

```html
<p>In 2007, Chris Wanstrath (<a href="https://github.com/defunkt" class="user-mention">@defunkt</a>),
PJ Hyett (<a href="https://github.com/pjhyett" class="user-mention">@pjhyett</a>),
and Tom Preston-Werner (<a href="https://github.com/mojombo" class="user-mention">@mojombo</a>)
founded GitHub.</p>
```

## Deployment to GitHub Pages

[GitHub Pages](https://pages.github.com/) are freely hosted by `GitHub` on its `github.io`. My personal page is [madrus.github.io](https://madrus.github.io).

Deployment itself -if all the installation and configuration steps are successfully completed- is actually very simple. Just push the new version to `master` branch and refresh your blog page.

## Enabling Travis and GitHub

Enabling Travis builds for your GitHub repository is pretty simple:

1. Go to your profile on travis-ci.org: [https://travis-ci.org/profile/username][5]
2. Find the repository for which you’re interested in enabling builds.
3. Click the slider on the right so it says “ON” and is a dark grey.
4. Optionally configure the build by clicking on the gear icon. Further configuration happens in your `.travis.yml` file.

[1]: https://madrus.github.io/
[2]: http://lanyon.getpoole.com/
[3]: https://github.com/poole/lanyon
[4]: https://www.youtube.com/watch?v=T2nx6tj-ZH4
[5]: https://travis-ci.org/profile/username

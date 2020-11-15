# 2020-02-02 How to Create a Blog Using Jekyll and GitHub Pages on Windows

Written on April 30th, 2020 by Sabina Akter

Jekyll has  **no admin interface** ,  **only source files**  that you can build using a CLI _(command line interface)_ to create a [static website](https://www.smashingmagazine.com/2015/11/modern-static-website-generators-next-big-thing/). Simply write your blog posts in [Markdown](https://www.markdownguide.org/) and if you choose to host your website using [GitHub Pages](https://pages.github.com/), you can use [Git](https://git-scm.com/) to commit and push your changes to publish new posts or pages.

Jekyll is easy to install on [macOS](https://www.apple.com/macos/catalina/) and [Linux](https://www.linux.org/), but there are a few extra steps required to be able to use Jekyll on Windows. This tutorial will guide you through:

- How to create a Jekyll blog on Windows
- Configuring your new Jekyll blog
- Writing posts and pages in Markdown
- Hosting your blog using GitHub Pages

**Prerequisites**

In order to follow along with this tutorial, you&#39;ll need to be using a recent version of the Windows operating system. You&#39;ll also need [Visual Studio Code](https://code.visualstudio.com/) _(or a similar code editor)_, [Git for Windows](https://gitforwindows.org/) _(or your favorite Git client)_ and a [GitHub](https://github.com/) account if you would like to use GitHub Pages.

**How to Install Jekyll on Windows**

Jekyll is written in Ruby as a [gem](https://rubygems.org/), so to run Jekyll on Windows we&#39;ll first need to download and install [RubyInstaller for Windows](https://rubyinstaller.org/). Make sure to download a recent  **Ruby+DevKit**  version and use the default options in the installation wizard. On the last step, you&#39;ll want to keep the option  **&quot;Run &#39;ridk install&#39; to setup MSYS2 and development toolchain.&quot;**  checked.

![](RackMultipart20201114-4-dpw22s_html_a7f6bfc114da35c2.png)

Completing the Ruby+DevKit with MSYS2 Setup Wizard

You&#39;ve almost installed Ruby on Windows! Once finished the installation wizard, you should see a command prompt to setup MSYS2 and the development toolchain. Simply enter  **1**  in the command prompt to install the MSYS2 base installation.

![](RackMultipart20201114-4-dpw22s_html_77d54aa448c2db53.png)Running _ridk install_ to setup MSYS2 and the development toolchain

You can now close the command prompt and open up a fresh one, because now that we have Ruby installed, it&#39;s time to install Jekyll! In the new command prompt, execute the command:

gem install jekyll bundler

![](RackMultipart20201114-4-dpw22s_html_9ed674f5ab2deb7f.png)Install the Ruby gems _jekyll_ and _bundler_

Let&#39;s confirm Jekyll is installed on Windows by outputting the version of Jekyll on our machine. To do this, run the command:

jekyll -v

![](RackMultipart20201114-4-dpw22s_html_6b7ae65e31b841cb.png)Confirm Jekyll has been installed successfully

Now you&#39;re ready to use Jekyll in the command line to create your new blog!

**How to Create a New Blog using Jekyll**

Using Jekyll we can  **use one command to create a new blog**  with a default theme, post and page. Create a new folder on your PC for your Jekyll blog and use it&#39;s full path as the parameter in the following command:

jekyll new PATH

![](RackMultipart20201114-4-dpw22s_html_f38e355bd61df566.png)Create a new blog using the _jekyll new_ command

Thats it! If you check the folder, Jekyll will have created the necessary files for your new blog; including the  **default ** [**Minima**](https://github.com/jekyll/minima) ** theme** , an example post and page and the default configuration settings.

**Let&#39;s see how it looks!**  I&#39;m going to use the free code editor [Visual Studio Code](https://code.visualstudio.com/) by [Microsoft](https://www.microsoft.com/) for the remainder of this tutorial to execute commands in a terminal _and_ be able to edit the Jekyll files in the same workspace.

**Tip**

For a list of useful Visual Studio Code extensions, check out my article [25+ Visual Studio Code Extensions That Are Worth Installing](https://kiltandcode.com/2020/02/02/visual-studio-code-extensions-that-are-worth-installing/).

Open the Jekyll folder in Visual Studio Code and create a new terminal _( __**Ctrl+`**__ )_. Now we can run the command to build and locally serve our Jekyll blog:

jekyll serve

![](RackMultipart20201114-4-dpw22s_html_730e84dd16b3194c.png)Run the _jekyll serve_ command to build and locally serve your Jekyll blog

Once Jekyll has used the source files to build the website, we can now use the server address generated by Jekyll to view our new blog locally in the browser.

![](RackMultipart20201114-4-dpw22s_html_96891ac266e336c9.png)Browse your Jekyll blog locally!

Congratulations! You now have a Jekyll blog using the default settings running locally on your PC.

**Configuration**

Remember I mentioned there is no admin interface? Instead Jekyll uses the _\_config.yml_ file located in the root of your Jekyll directory to configure your website. The _\_config.yml_ file is written in [YAML](https://yaml.org/) _(YAML Ain&#39;t Markup Language)_, a human friendly data-serialization language.

**Default Settings**

Below are the default settings in the _\_config.yml_ file. Make sure to change the default  **&quot;Your awesome title&quot;**  to the title of your blog or website, as well as your email address and an interesting description of the subject of your blog.

# this is your awesome title&quot;

title: techformbd

email: your-email@example.com

description: \&gt;- # this means to ignore newlines until &quot;baseurl:&quot;

Write an awesome description for your new site here. You can edit this

line in \_config.yml. It will appear in your document head meta (for

Google search results) and in your feed.xml site description.

baseurl: &quot;&quot;# the subpath of your site, e.g. /blog

url: &quot;&quot;# the base hostname &amp; protocol for your site, e.g. http://example.com

twitter\_username: jekyllrb

github\_username: jekyll

# Build settings

theme: minima

plugins:

- jekyll-feed

**Baseurl and Url**

The  **baseurl**  setting is only used if your blog or website is  **not**  going to sit at the root of your domain name. For example, if your Jekyll website will be at _https://techforumbd.github.io/,_leave the baseurl blank. If your blog or website will be at _https://techforumbd.github.io/techforum/_, enter  **/techforum**  as the baseurl.

The  **url**  setting is what Jekyll uses to determine the domain name of your website. For example, the Jekyll website you are currently on uses the domain name  **https://techforumbd.com** , so that&#39;s the url value used for this website.

**Themes and Layouts**

Jekyll uses the [Minima](https://github.com/jekyll/minima) theme by default, but this can easily be changed. As is the case with many blogging platforms, there are plenty of  **pre-built themes**  out there if you don&#39;t fancy building your own. [Jekyll Themes](https://jekyllthemes.io/) is an excellent curated directory of free _(and paid)_ Jekyll themes that&#39;s definitely worth checking out!

![](RackMultipart20201114-4-dpw22s_html_49b0b88f25f2844f.png)

[Jekyll Themes](https://jekyllthemes.io/) - a curated directory of Jekyll themes

If you want to build your own theme,  **Jekyll uses the ** [**Liquid**](https://shopify.github.io/liquid/) ** syntax**  to be able to do things like display a list of your latest blog posts, write your own pagination, almost anything you would want a good blogging platform to be able to do.

In addition to themes, Jekyll also uses  **layouts**  to enable you to write _(or customize)_ the [HTML](https://www.w3schools.com/html/), [CSS](https://www.w3schools.com/css/default.asp) and [JavaScript](https://www.w3schools.com/js/default.asp) used on your website. You&#39;re in control!

Check out the [themes](https://jekyllrb.com/docs/themes/) and [layouts](https://jekyllrb.com/docs/layouts/) documentation on the Jekyll website to learn more.

**Permalinks**

Have you ever used WordPress, or a similar blogging platform to customize the permalink style used to link to your blog posts? Jekyll can do this as well! In my opinion, this really does demonstrate how Jekyll was built to be a great blogging platform.

Simply add one of the below to your configuration file to apply the permalink style to your blog:

_https://kiltandcode.com/jekyll/2020/04/30/how-to-create-a-blog-using-jekyll-and-github-pages-on-windows/_

permalink: /:categories/:year/:month/:day/:title/

_https://kiltandcode.com/2020/04/30/how-to-create-a-blog-using-jekyll-and-github-pages-on-windows/_

permalink: /:year/:month/:day/:title/

_https://kiltandcode.com/how-to-create-a-blog-using-jekyll-and-github-pages-on-windows/_

permalink: /:title/

**Plugins**

You&#39;ll notice in the default configuration file there is a plugin already referenced:  **&quot;jekyll-feed&quot;**. This is just one of the many plugins available for Jekyll that can provide useful functionality to your blog. The [jekyll-feed](https://github.com/jekyll/jekyll-feed) plugin will generate an Atom _(RSS-like)_ feed for readers to be able to subscribe to your blog.

To install a Jekyll plugin, you will need to add the name of the plugin in two places. The first is in the _&quot;plugins&quot;_ section of the  **\_config.yml**  file, and the second is in the  **&quot;Gemfile&quot;**. The [_Gemfile_](https://bundler.io/gemfile.html) is what Ruby uses to determine the gem dependencies required to execute Ruby code.

There&#39;s also many other plugins available, such as [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) that will automatically add search-optimized metadata to your HTML to give you that extra boost in the search rankings _(this is my personal favorite!)_. Just remember, GitHub Pages only supports a short list of plugins, so be sure to checkout the list of [supported plugins](https://pages.github.com/versions/) before using GitHub Pages to host your website.

**Posts**

If you&#39;ve made it this far, you&#39;re probably wondering when we&#39;re going to get to the good stuff! This is why I, like many, migrated to Jekyll. The simplicity of writing interesting blog posts!

**Filename Structure**

In the list of files that Jekyll creates using the _jekyll new_ command there is a  **&quot;\_posts&quot;**  folder. This is where Jekyll will look for blog posts when it builds your website, so be sure to add any new posts in this folder so Jekyll can find them.

![](RackMultipart20201114-4-dpw22s_html_b5b1bb177b6b3bb1.png)Markdown file in Visual Studio Code

When writing new blog posts, be sure to use the file format:

**YEAR-MONTH-DAY-title.MARKUP**

**YEAR**  is a four digit number and  **MONTH**  and  **DAY**  are two digit numbers. So, for the blog post _&quot;10 Reasons Why Jekyll is Awesome&quot;_ written on the 1st of April 2020, the filename would be  **&quot;2020-04-01-10-reasons-why-jekyll-is-awesome.markdown&quot;**.

**Front Matter**

While first introduced in Jekyll, front matter is used in the majority of static site generators, such as the popular [GatsbyJS](https://www.gatsbyjs.org/) and [Hugo](https://gohugo.io/).

It&#39;s a simple way of adding information about the post or page to the top of the document. In the below front matter you will see:

- The layout used for the document
- The title of the document
- The date the document was published
- A list of categories the document belongs to

---

layout: post

title: &quot;WelcometoJekyll!&quot;

date: 2020-04-15 15:19:23 -0700

categories: jekyll update

---

**Other examples of Jekyll front matter are:**

If you would prefer a specific permalink to be used instead of the default:

permalink: /jekyll-is-awesome/

If you would like Jekyll to ignore a post until it&#39;s ready to be published:

published: false

**Markdown**

Let&#39;s get writing! When you are ready to write your blog post, you can use [Markdown](https://www.markdownguide.org/Markdown) to add rich text formatting to your documents. Created by [John Gruber](https://twitter.com/gruber) of [Daring Fireball](https://daringfireball.net/), Markdown is a markup language that will convert basic syntax to HTML.

Here are a few examples you can use in your blog posts:

**Headers ** _**(H1, H2, H3, H4, H5, H6)**_

**# H1**

## H2

### H3

#### H4

##### H5

###### H6

**Bold text**

\*\*text\*\*

**Italic text**

\*text\*

**Hyperlinks**

[Google](https://google.com)

**Images**

![Screenshot](screenshot.jpg)

**Pages**

Jekyll also supports  **pages for standalone content that isn&#39;t date based** , such as an about or contact page. You can also use the [liquid syntax](https://jekyllrb.com/docs/liquid/) to create pages with custom functionality, such as a searchable list of all your blog posts.

Similar to posts, front matter can be used to add information to your page:

---

layout: page

title: About

permalink: /about/

---

**Pages are stored in the root directory**  of your website as either Markdown or HTML documents. You can also add pages into sub-folders in your root directory and Jekyll will take into account the sub-folder when the site is built.

**GitHub Pages**

Because Jekyll was built by [Tom Preston-Werner](https://tom.preston-werner.com/), the co-founder of [GitHub](https://github.com/), Jekyll works exceptionally well with [GitHub Pages](https://pages.github.com/).

GitHub Pages is a static website hosting service that enables you to host a _(static)_ website directly from a public GitHub repository. At the time of writing, it is available on GitHub Free, GitHub Free for organizations as well as the professional and enterprise plans.

One of the great benefits of using Jekyll with GitHub Pages is that you can write a new blog post, commit it to the GitHub repository that&#39;s being used to host your blog and  **your website will be automatically built to publish the new article**. This is why Jekyll and GitHub Pages work so well together!

Let&#39;s create a new GitHub repository so we can publish our new Jekyll blog on GitHub Pages. In your GitHub account, create the repository _ **username** _.github.io, making sure _ **username** _ is the username of your GitHub account.

![](RackMultipart20201114-4-dpw22s_html_20acef7edfa5c3ed.png)

Creating a new repository on GitHub

Clone the new repository to your PC using git:

git clone https://github.com/username/username.github.io

Copy and paste all your Jekyll files into the new local repository on your PC and push your changes to the repository:

git add --all

git commit -m &quot;Initial commit of Jekyll blog&quot;

git push -u origin master

That&#39;s it! You&#39;ll now be able to view your Jekyll blog at the address https://username.github.io.
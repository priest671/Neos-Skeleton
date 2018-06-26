# Code Q Neos-Skeleton

The Neos-Skeleton provides a easy and powerful start for new projects - beginner-friendly and highly scalable. It implements all current best practises for Neos 4 and is frontend tooling agnostic.

It combines contributions of some of the best Neos developers with experience from Code Q. It is inspired by [Flowpack Neos best practise examples (Dmitri Pisarev and Dominique Feyer)](https://github.com/Flowpack/fusion-bp) and the [single repro setup (Christian Müller)](https://github.com/kitsunet/composer-install-testing).


## Feature overview

 - A powerfull best practise layout rendering machanism
 - Best practise folder and naming structure
 - A well rounded set of packages to build typical websites

## Further boilerplate features

 - [YAML Constraints](https://www.youtube.com/watch?v=ZCRYsYvxXFI) to easily manage where node types should be available
 - It provides the most used smartphone and tablet sizes as preview modes
 - All rendering is based on Fusion and AFX

## Features via required packages

 - [neos/seo](https://github.com/neos/neos-seo) allows your to configure SEO and social media settings
 - [neos/redirecthandler-neosadapter](https://github.com/neos/redirecthandler-neosadapter) automatically creates a redirect when you change/move a page
 - [neos/neos-googleanalytics](https://github.com/neos/neos-googleanalytics) adds your Google Analtics tracking code
 - [carbon/compression](https://github.com/CarbonPackages/Carbon.Compression) compresses the HTML output
 - [carbon/hyphen](https://github.com/CarbonPackages/Carbon.Hyphen) allows editors to add shy characters
 - [codeq/unicodenormalizer](https://github.com/code-q-web-factory/neos-unicodenormalizer) handles broken German Umlaute
 - [flowpack/cachebuster](https://github.com/Flowpack/Flowpack.CacheBuster) adds automatic cache busting for assets in the frontend
 - [moc/notfound](https://github.com/mocdk/MOC.NotFound) loads a normal editable page for displaying a 404 error
 - [jonnitto/sitemap](https://github.com/jonnitto/Jonnitto.Sitemap) improves the XML sitemap
 - [neos/nodetypes-contentreferences](https://github.com/neos/nodetypes-contentreferences) provides a reference content node type
 
## Development features via required packages

 - [carbon/link](https://github.com/jonnitto/Carbon.Link) provides powerfull link helpers
 - [sitegeist/silhouettes](https://github.com/sitegeist/Sitegeist.Silhouettes) let's you preconfigure property-silhouettes that can be applied to various properties of multiple NodeTypes in a better way then mixins.
 - [ttree/eelshell](https://github.com/ttreeagency/EelShell) let's you try your eel expressions in the terminal
 - [sitegeist/neosguidelines](https://github.com/sitegeist/Sitegeist.NeosGuidelines) validates that you follow the in [Settings.PreviewModes.yaml](DistributionPackages/CodeQ.Site/Configuration/Settings.PreviewModes.yaml) defined code conventions
 - [carbon/includeassets](https://github.com/CarbonPackages/Carbon.IncludeAssets) provides an easy way to include your assets (css, js)


## Steps to get started

Requirements:
Your local development environment must provide [a webserver like Apache or nginx, PHP 7.1+, composer and MySQL 5.7.x or MariaDB 10.2.x](https://www.neos.io/download-and-extend.html).

__Start a new git project__

1. Clone this repository `git clone git@github.com:code-q-web-factory/Neos-Skeleton.git PROJECTNAME`
2. Replace the Package name "CodeQ.Site" with your own company name. We recommend to keep ".Site" for all projects to easily copy code from one project to another.
3. Create a new git project on the server of your choice, in our example Github
4. Start the new git project locally and push the initial state
    ```
    cd PROJECTNAME
    rm -rf .git && git init
    git remote add origin git@github.com:PROJECTNAME.git
    git fetch
    git add .
    composer install
    git commit -m "TASK: Copy from Neos-Skeleton"
    git push -u origin master
    ```

__Run the project locallly__

5. Start your database server.
6. Start the local server in the terminal:
    ```
    ./flow server:run
    ```
7. Setup the database configuration and initial content at [http://127.0.0.1:8081/setup](http://127.0.0.1:8081/setup), there import the initial content from the package CodeQ.Site.

__Configure your project__

8. Configure the Google Analytics tracking code in [Production/Settings.yaml](DistributionPackages/CodeQ.Site/Configuration/Production/Settings.yaml) in the format `UA-XXXXXXXX-X`
9. German is the default language, you can adopt it in [Settings.Language.yaml](DistributionPackages/CodeQ.Site/Configuration/Settings.Language.yaml)
10. In the Neos administration create a new page with the url path segment "404", this page will be used every time a page couldn't be found.

__Start developing__

11. Copy your preferred frontend tooling into Resources/Public/Frontend and adopt the include assets pathes in [Settings.IncludeAssets.yaml](DistributionPackages/CodeQ.Site/Configuration/Settings.IncludeAssets.yaml)
12. Create your own document and content node types and add the styles to your CSS.

__Tip:__
Folow the [Code Q Code Conventions](https://docs.google.com/document/d/13ykoM0Ta2qJvO_6BYa-DIsx7_MxFsInOSbJqJHuINBw/edit?usp=sharing) and validate your code with
```
./flow configuration:validate
./flow guidelines:validateDistribution
./flow guidelines:validatePackages
```

## How the layout mechanism works

For rendering documents we use the [Neos 4 document rendering](http://neos.readthedocs.io/en/stable/CreatingASite/RenderingCustomMarkup/PageRendering.html), just create a Fusion object similar to [Page.fusion](DistributionPackages/CodeQ.Site/Resources/Private/Fusion/Document/Page/Page.fusion) with the same name as your node type.

All documents should inherit from [AbstractPage.fusion](DistributionPackages/CodeQ.Site/Resources/Private/Fusion/Document/AbstractPage/AbstractPage.fusion) and then by default use the [DefaultLayout.fusion](DistributionPackages/CodeQ.Site/Resources/Private/Fusion/Component/DefaultLayout/DefaultLayout.fusion). The default layout allows you to customize the layout in a central place.


## You need help?

For questions about the boilerplate feel free to write in the Slack channel #general and tag me with @rolandschuetz

The development of this boilerpalte is sponsored by [Code Q](https://codeq.at/de/kontakt). We can consult your company on Neos setups and build processes. Get in contact: rs@codeq.at


## License

The MIT License (MIT)

Copyright (c) 2016 Neos-Skeleton contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

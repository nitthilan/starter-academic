<p align="center"><a href="https://wowchemy.com" target="_blank" rel="noopener"><img src="https://wowchemy.com/img/logo_200px.png" alt="Wowchemy Website Builder"></a></p>

# Academic Template for [Hugo](https://github.com/gohugoio/hugo)

The Hugo **Academic Resumé Template** empowers you to create your job-winning online resumé and showcase your academic publications.

[Check out the latest demo](https://academic-demo.netlify.app) of what you'll get in less than 10 minutes, or [view the showcase](https://wowchemy.com/user-stories/).

[**Wowchemy**](https://wowchemy.com) makes it easy to create a beautiful website for free. Edit your site in Markdown, Jupyter, or RStudio (via Blogdown), generate it with Hugo, and deploy with GitHub or Netlify. Customize anything on your site with widgets, themes, and language packs.

- 👉 [**Get Started**](https://wowchemy.com/docs/install/)
- 📚 [View the **documentation**](https://wowchemy.com/docs/)
- 💬 [Chat with the **Wowchemy community**](https://discord.gg/z8wNYzb) or [**Hugo community**](https://discourse.gohugo.io)
- 🐦 Twitter: [@wowchemy](https://twitter.com/wowchemy) [@GeorgeCushen](https://twitter.com/GeorgeCushen) [#MadeWithWowchemy](https://twitter.com/search?q=(%23MadeWithWowchemy%20OR%20%23MadeWithAcademic)&src=typed_query)
- 💡 [Request a **feature** or report a **bug** for _Wowchemy_](https://github.com/wowchemy/wowchemy-hugo-modules/issues)
- ⬆️ **Updating Wowchemy?** View the [Update Guide](https://wowchemy.com/docs/update/) and [Release Notes](https://wowchemy.com/updates/)

## Crowd-funded open-source software

To help us develop this template and software sustainably under the MIT license, we ask all individuals and businesses that use it to help support its ongoing maintenance and development via sponsorship.

### [❤️ Click here to unlock rewards with sponsorship](https://wowchemy.com/plans/)

## Ecosystem

* **[Wowchemy Admin](https://github.com/wowchemy/wowchemy-admin/):** An admin tool to import publications from BibTeX

[![Screenshot](https://raw.githubusercontent.com/wowchemy/wowchemy-hugo-modules/master/academic.png)](https://wowchemy.com)

<!--
[![Analytics](https://ga-beacon.appspot.com/UA-78646709-2/academic-kickstart/readme?pixel)](https://github.com/igrigorik/ga-beacon)
-->

https://search.google.com/search-console?resource_id=https%3A%2F%2Fnitthilan.github.io%2F
https://analytics.google.com/analytics/web/#/realtime/rt-location/a178463631w246867066p229280192/


HUGO_VERSION = "0.78.2"
wget https://github.com/gohugoio/hugo/releases/download/v0.78.2/hugo_extended_0.78.2_Linux-64bit.deb
apt remove hugo
apt install ./hugo_extended_0.78.2_Linux-64bit.deb 

export PATH=$PATH:/usr/local/go/bin - Install go and export path

hugo server

git add .
git commit -m "Initial commit"
git push -u origin master

hugo mod clean
hugo mod get -u ./...

hugo
cd public
git add .
git commit -m "Build website"
git push origin master
cd ..

List of things to do:
- Add source code for papers
- Add all the project  details for work done earlier [https://docs.google.com/document/d/1uGKzp_z_d9yr-X-y1aADYFB2vxoFWapEWY9KHAT5sU8/edit]
- Move patents to main page if possible

Errors faced:
- "template for shortcode "callout" not found" - https://discourse.gohugo.io/t/academic-theme-failed-to-extract-shortcode-template-for-shortcode-callout-not-found/28857/3


podman run -it --rm --ipc=host -v /local/data/nitthilan/:/nitthilan/ --name nitt_hugo docker.io/klakegg/hugo 


curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&&  apt update \
&&  apt install gh -y


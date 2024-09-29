# lba-engine-architecture
Little Big Adventure series Engine Architecture documentation community-driven

[Live Documentation](https://lbalab.github.io/lba-engine-architecture/)

## Introduction

The Little Big Adventure Series Engine Architecture is a project to document and teach how Adeline Software International implement their games, including Little Big Adventure 1 (Relentless: Twinsen's Adventure), Little Big Adventure 2 (Twinsen's Odyssey) and Time Commando.

This documentation will refer to the engines open-sourced and reimplemented by the community, such as [lba1-classic-community](https://github.com/LBALab/lba1-classic-community), [lba2-classic-community](https://github.com/LBALab/lba2-classic-community), [twin-e](https://github.com/LBALab/twin-e), [twine ScummVM](https://github.com/scummvm/scummvm/tree/master/engines/twine).

## Copyright
The intellectual property is currently owned by [2.21]. Copyright [2.21]

Originaly developed by Adeline Software International in 1994 (LBA1), Time Commando (1996) and LBA2 (1997).

### Licence
This documentation is licensed under MIT.

The source code for both games that has been release by [2.21] has been licensed under the GNU General Public License.

Please note theses licenses do not apply to Little Big Adventure 1 & 2 or Time Commando game assets (art, models, textures, audio, etc.) are not open-sourced and therefore aren't redistributable.



## Get Started

### How can I contribute

Fork the projct to your own repository, make your changes and submit a pull request. If you are not familiar with git you can try editing the files directly on GitHub or drop us a message on Discord.

If you need help to get you started with this project, you can join us on [Discord](https://discord.gg/gfzna5SfZ5).

### Install Jekyll and Bundler

If you don't have Jekyll installed, you can install it by running the following command:

```bash
gem update --system
gem install jekyll bundler
```

### Building and previewing your site locally

Assuming [Jekyll] and [Bundler] are installed on your computer:

1.  Change your working directory to the root directory of your site.

2.  Run `bundle install`.

3.  Run `bundle exec jekyll serve --watch` to build your site and preview it at `localhost:4000`.

    The built site is stored in the directory `_site`.

Once changes are commited to the repository, the site will be automatically built and deployed to GitHub Pages under the URL: https://lbalab.github.io/lba-engine-architecture/

# Team Colors

This Team Colors is a fork from [Team Colors](http://jim-nielsen.com/teamcolors) is a reference of HEX values for the brand colors of japanese high school baseball teams.

## How-To

Install project dependencies via npm:

```
npm install
```

### Development

To actively develop, run:

```
npm run dev
```

This will setup Webpack and Sass to compile javascript and CSS into the `build` folder. Hitting the root of this folder from your localhost will serve your files.

### Deployment

The production site at [jim-nielsen.com/teamcolors](http://jim-nielsen.com/teamcolors) runs on github pages so all static assets must be generated and pushed with the repo. To deploy, run:

```
npm run prod
```
**Note:**

- Everything in `/static` are static files that are referenced directly via the HTML file. So if you make a commit that changes these, they’ll be pulled in automatically without having to do a “build” of the site and committing that as well. For example, if somebody makes a PR that changes a color value in the team colors .json file, you can merge the PR from github and changes should be live to the site without having to actually run a build.
- Everything in `/build` has to be built when you make an interactive/stylistic change in javascript or CSS. Change some css? Compile it to `/build/styles` and commit. Change some javascript, i.e. the way the app works? Compile it to `/build/scripts`. Raw assets like images and data are pulled in from `/static`.

## Technical Overview

Site is built on the react framework. `index.html` is the shell container for react app. If javascript is not supported, a link is shown to the raw JSON data which has all color information.

Color data is housed in a single `.json` file `static/data/teams.json`. Any changes to team colors can be done there. *Note on colors*: Color definitions for each team are in arrays and grouped by color mode. Color values should match index position in the array across color modes, for example:

```
colors:
  rgb: TEAMS-RGB-BLUE, TEAMS-RGB-RED
  hex: TEAMS-HEX-BLUE, TEAMS-HEX-RED
```

Source artwork for each team is grouped by league in `static/sketch`. Production versions of these logo should be in `.svg` format in `static/img`.

### Edit Team Color or Name

Find teams `.json` file in `static/data/teams.json`, and edit the info you need.

### Add a Team

1. Determine the school’s prefecture
2. Following the established pattern, add the school’s name and colors the `.json` file
3. Run `npm run prod`, commit, push



# Maintainer

* Morbus Iff <<morbus@disobey.com>>

# Dependency installation

```bash
mkdir lib && cd lib

git clone git@github.com:Dan-Q/twee2.git
cd twee2
gem build twee2.gemspec
gem install twee2-0.5.0.gem

# TODO: Add patch information.
hg clone ssh://hg@bitbucket.org/mcdemarco/dotgraph
cd dotgraph
npm install
grunt package
```

# Choicemap generation

```bash
cd choicemaps/TITLE
twee2 build --format=../../lib/dotgraph/dist/Twine2/online/DotGraph TITLE.tw2 TITLE.html
```

Then:

  1. Open the `.html` file in your browser.
  2. Fiddle with the settings until the choicemap looks good.
  3. Codify the settings in the StorySettings passage in the `.tw2`.
  4. "Save Source" the DOT source into a properly named `.gv` file.
  5. "Save Image" the SVG into a properly named `.svg` file.
  6. Convert the SVG to PNG with `inkscape -z TITLE.svg -e TITLE.png`

# TODO

* When it comes to apps, we need more details in the title or GBCMDetails metadata.
* We should detail the allowed valuesa for GBCMDetails in the README.md.
* Alphabetize tags when "Color by tag" is enabled?

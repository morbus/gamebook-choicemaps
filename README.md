
# Maintainer

* Morbus Iff <<morbus@disobey.com>>

Gamebook Choicemaps is aptly named as it is a collection of gamebook choicemaps
in multiple parsable formats:

  1. `TITLE.tw2`: a plain-text readable file [in Twee2 format](https://dan-q.github.io/twee2/)
  2. `TITLE.gv`: a DOT file for use with [Graphviz](http://www.graphviz.org/) and other readers
  3. `TITLE.svg`: a render of the DOT file in SVG format
  3. `TITLE.png`: a conversion of the SVG file to PNG format

The following choicemaps are currently available:

Title | Year | Generated formats
------|------|-----
CYOA: The Haunted House | 2007 | ...
Endless Quest: Big Trouble | 2018 | [TW2](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.tw2) • [DOT](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.gv) • [SVG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.svg) • [PNG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.png)
Investigations in Lovecraft Country #1: Alone Against the Flames | 2018 | ...

# Generating a choicemap

## Dependency installation

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

## Choicemap generation

Write your choicemap as a Twee2 file.

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

* DotGraph: Alphabetize tags when "Color by tag" is enabled?
* README.md: Need an intro to the "Generating a choicemap" section.
* README.md: Document the allowed values for the GBCMDetails passage.
* README.md: Finish documenting how to generate your own choicemap.
* GBCMDetails: We need more details in the title or metadata.

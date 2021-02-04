
# Gamebook Choicemaps

* Morbus Iff <<morbus@disobey.com>>

This is a collection of gamebook choicemaps in multiple formats:

  1. `TITLE.tw2`: a plain-text readable file [in Twee2 format](https://dan-q.github.io/twee2/)
  2. `TITLE.gv`: a DOT file for use with [Graphviz](http://www.graphviz.org/) and other readers
  3. `TITLE.svg`: a render of the DOT file in SVG format
  3. `TITLE.png`: a conversion of the SVG file to PNG format

The following choicemaps are currently available:

| Gamebook title | Buy | Available choicemaps |
|----------------|-----|----------------------|
| Endless Quest #52: Big Trouble (2018) | [Amazon](https://amzn.to/3az0Eiu) | [TW2](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.tw2) • [DOT](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.gv) • [SVG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.svg) • [PNG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.png) |
| Choose Your Own Adventure: The Haunted House (2007) | [Amazon](https://amzn.to/3ja6A58) | [TW2](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.tw2) • [DOT](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.gv) • [SVG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.svg) • [PNG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.png) |

## Generating a choicemap

### Dependency installation

```bash
mkdir bin && cd bin

# Twee2 from https://dan-q.github.io/twee2/.
git clone git@github.com:Dan-Q/twee2.git
cd twee2
gem build twee2.gemspec
sudo gem install twee2-0.5.0.gem

# DotGraph from http://mcdemarco.net/tools/scree/dotgraph/.
git clone git@github.com:mcdemarco/dotgraph.git
cd dotgraph
npm install
grunt package

# Install inkscape via your OS's package manager for SVG to PNG conversion.
# For OS X, the quickest success was with brew and "brew install inkscape".
```

### Choicemap generation

Write your choicemap as a Twee2 file, then export it into DotGraph as:

```bash
cd choicemaps/TITLE
twee2 build --format=../../bin/dotgraph/dist/Twine2/online/DotGraph TITLE.tw2 TITLE.html
```

Then:

  1. Open the `.html` file in your browser.
  2. Fiddle with the settings until the choicemap looks good.
  3. Codify the settings in the `DotGraphSettings` passage in the `.tw2`.
  5. "Save Image" the SVG into a properly named `.svg` file.
  4. "Save Source" the DOT source into a properly named `.gv` file.
  6. Convert the SVG to PNG with `inkscape --export-type=png --export-dpi=300 TITLE.svg`

# TODO

* DotGraph: Alphabetize tags when "Color by tag" is enabled?
* README.md: Need an intro to the "Generating a choicemap" section.
* README.md: Document the allowed values for the GBCMDetails passage.
* README.md: Finish documenting how to generate your own choicemap.
* README.md: Add note about wordy file naming scheme.
* Replace .gitignore with your current standard monstrosity.
* Replace the iOS Alone Against the Flames with the Chaosium PDF version?

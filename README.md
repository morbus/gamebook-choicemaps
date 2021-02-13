
# Gamebook Choicemaps

* Morbus Iff <<morbus@disobey.com>>

This is a collection of gamebook choicemaps in multiple formats:

  1. `TITLE.twee`: a plain-text readable file [in Twee3 format](https://github.com/iftechfoundation/twine-specs/blob/master/twee-3-specification.md).
  2. `TITLE.gv`: a DOT file for use with [Graphviz](http://www.graphviz.org/) and other readers.
  3. `TITLE.svg`: a render of the DOT file in SVG format.
  3. `TITLE.png`: a conversion of the SVG file to PNG format.

The following choicemaps are currently available:

| Gamebook title | Buy | Available choicemaps |
|----------------|-----|----------------------|
| Endless Quest #52: Big Trouble (2018) | [Amazon](https://amzn.to/3az0Eiu) | [TWEE](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.twee) • [DOT](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.gv) • [SVG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.svg) • [PNG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/big-trouble--2018--isbn-9781536202441/big-trouble--2018--isbn-9781536202441.png) |
| Choose Your Own Adventure: The Haunted House (2007) | [Amazon](https://amzn.to/3ja6A58) | [TWEE](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.twee) • [DOT](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.gv) • [SVG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.svg) • [PNG](https://raw.githubusercontent.com/morbus/gamebook-choicemaps/master/choicemaps/the-haunted-house--2007-reissue--isbn-9781933390512/the-haunted-house--2007-reissue--isbn-9781933390512.png) |

## Generating a choicemap

### Dependency installation

```bash
# All dependencies go in bin.
mkdir bin bin/storyformats
cd bin

# Tweego from https://www.motoslave.net/tweego/.
git clone https://github.com/tmedwards/tweego.git
cd tweego
go get
go build
mv tweego /usr/local/bin/tweego
cd ..

# DotGraph story format from http://mcdemarco.net/tools/scree/dotgraph/.
git clone git@github.com:mcdemarco/dotgraph.git
cd dotgraph
npm install
grunt package
cp -R dist/Twine2/offline/DotGraph ../storyformats

# SugarCube story format from http://www.motoslave.net/sugarcube/2/.
cd ../storyformats
curl -LO https://github.com/tmedwards/sugarcube-2/releases/download/v2.34.1/sugarcube-2.34.1-for-twine-2.1-local.zip
unzip sugarcube-2.34.1-for-twine-2.1-local.zip
rm sugarcube-2.34.1-for-twine-2.1-local.zip

# Confirm that tweego can see the installed story formats.
# Add absolute path TWEEGO_PATH to your env for shorter commands.
cd ../../
TWEEGO_PATH=bin/storyformats tweego --list-formats
 
# Install inkscape for SVG to PNG conversion.
# For OS X, the quickest success was with "brew install inkscape".
```

### Choicemap generation

Write your choicemap as a Twee3 file, then export it into DotGraph as:

```bash
cd choicemaps/TITLE
tweego --format DotGraph --output TITLE.html TITLE.twee
```

Then:

  1. Open the `.html` file in your browser.
  2. Fiddle with the settings until the choicemap looks good.
  3. Codify the settings in the `DotGraphSettings` passage in the `.twee`.
  5. "Save Image" the SVG into a properly named `.svg` file.
  4. "Save Source" the DOT source into a properly named `.gv` file.
  6. Convert the SVG to PNG with `inkscape --export-type=png --export-dpi=300 TITLE.svg`

# TODO

* DotGraph: Alphabetize tags when "Color by tag" is enabled?
* README.md: Need an intro to the "Generating a choicemap" section.
* README.md: Document the allowed values for the GBCMDetails passage.
* README.md: Finish documenting how to generate your own choicemap.
* README.md: Add note about wordy file naming scheme?
* Replace .gitignore with your current standard monstrosity.
* Replace the iOS Alone Against the Flames with the Chaosium PDF version?
* Can we use tag-colors in twee3 for DotGraph tag colors?


# Maintainer

* Morbus Iff <<morbus@disobey.com>>

# Dependency installation

```bash
mkdir lib && cd lib

# TODO: Add patch information.
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
twee2 \
 build --format=lib/dotgraph/dist/Twine2/online/DotGraph/ \
 choicemaps/TITLE/TITLE.tw2 \
 choicemaps/TITLE/TITLE.html
```

# TODO

* When it comes to apps, we need more details in the title or GBCMDetails metadata.
* We should detail the allowed valuesa for GBCMDetails in the README.md.
* Alphabetize tags when "Color by tag" is enabled?

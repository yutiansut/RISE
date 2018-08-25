## Releases

Instructions and notes for preparing and publishing a release.

### Pre-Release check

**Step 1.** Clean your local repo copy:

    git clean -fdx

**Step 2.** Build the JS and CSS:

    npm install
    npm run build
    npm run build-css

**Step 3.** Check for updated version numbers in

* `package.json`

### Release

**Step 4.** Tag the repo with:

    git tag -a release_tag -m "Release msg"
    git push origin release_tag

**Step 5.** Build sdist and wheels packages:

    python setup.py sdist
    python setup.py bdist_wheel

**Step 6.** Upload *sdist* and *wheels* to PyPI:

    twine upload dist/*

**Step 7.** Update the version and the sha256 hash at
<https://github.com/conda-forge/rise-feedstock/blob/master/recipe/meta.yaml>
and open a PR with those changes. When the PR is merged, several CI runs will
be triggered and packages will be generated and uploaded to
<https://anaconda.org/conda-forge/rise/files>.

**NOTE**: Eventually, you would need to rerender the feedstock.
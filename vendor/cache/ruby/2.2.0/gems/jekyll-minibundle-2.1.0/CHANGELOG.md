# 2.1.0 / 2016-05-04

* Allow attributes without values. Useful for `async` attribute, for
  example. Pull Request #7 by Sam (@codewisdom).
* Ensure attribute value conversion to string

# 2.0.1 / 2016-04-06

* Fix Jekyll version requirement check to be more reliable

# 2.0.0 / 2016-04-01

* Drop support for Jekyll versions below 3
* Remove unused asset cache entries and temporary files when Jekyll
  rebuilds the site
* Document a known caveat: the plugin doesn't work with Jekyll's
  incremental rebuild feature.

# 1.6.0 / 2016-03-26

* Log the last 2000 bytes of minifier's STDOUT output if the minifier
  command fails. Pull Request #6 by Martin Nordholts (@Enselic).
* Allow prepending base URL for the destination path of `minibundle`
  block
* Drop Ruby MRI 1.9 support because Jekyll 3 does not support it
* Fix issues in asset reloading in Jekyll's watch (auto-regeneration)
  mode, doing bundling and asset fingerprinting again

# 1.5.1 / 2015-01-29

* Improve future compatibility with Jekyll. Minibundle has classes
  adhering to `Jekyll::StaticFile` interface, and some method
  implementations of the interface were missing.
* Small refactorings and test improvements

# 1.5.0 / 2014-07-27

* Support minifier command specification in `_config.yml` and inside
  `minibundle` block. Issue #4 by Phillip Smith (@phillipadsmith).
* Support enabling development mode from `_config.yml`
* Add argument validation to `minibundle` block and `ministamp` tag
* Document how to load the gem with Jekyll's `gems` config setting

# 1.4.6 / 2014-05-10

* Handle compatibility issues with safe_yaml and logger flexibly. This
  should allow using the plugin with Jekyll 1.0 and 2.0.

# 1.4.5 / 2014-05-10

* Use SafeYAML to load user input from `minibundle` block for
  consistent behavior with Jekyll and for security
* Clean log messages: show relative paths when bundling assets
* Add missing implementations of `relative_path` and `to_liquid`
  methods from Jekyll's StaticFile API (introduced in Jekyll v1.5.0),
  allowing Minibundle to behave better with other Jekyll
  plugins. Issue #3 by Michael Rose (@mmistakes).
* Fix Ruby deprecation warnings (use `File.exist?` instead of
  `File.exists?`)

# 1.4.4 / 2014-01-16

* Conserve memory when calculating fingerprint for an asset.
  Previously, we read the whole asset file into memory and then
  calculated the MD5 digest. This is bad for big assets. Now, we read
  the file in chunks.

# 1.4.3 / 2014-01-16

* Do not leak read pipe file descriptor upon minifier command failure
* Loosen version constraints for development gem dependencies
* Clarify documentation
* Fix some Ruby coding style issues
* Minor internal state handling improvements
* Clarify tests, increase test coverage

# 1.4.2 / 2013-12-28

* Ensure touching asset source triggers destination write. This was an
  unintentional edge case earlier. Now the behavior of touching the
  asset source is consistent with when changing the contents of the
  source.
* Separate tags produced by `minibundle` in development mode with
  newlines
* Clarify tests, increase coverage

# 1.4.1 / 2013-12-27

* Add missing files to gem package

# 1.4.0 / 2013-12-27

* Fix bug causing exception to be thrown when `ministamp` or
  `minibundle` is called twice with same asset source argument. Allow
  handling asset source files that are already static files in Jekyll
  (remove the restriction introduced in 1.3.0). Issue #2 by Austin
  Grigg (@agrigg).

# 1.3.0 / 2013-12-25

* Disallow handling asset source files that are already static files
  in Jekyll. Otherwise, we would potentially get to inconsistencies in
  Jekyll's watch mode. See "Jekyll static file restriction" in
  README.md. Issue #2 by Austin Grigg (@agrigg).
* Upgrade development dependencies

# 1.2.0 / 2013-09-29

* If Jekyll's logger is available, use it for nice output when bundling
* Upgrade development dependencies
* Simplify `BundleFile` class implementation

# 1.1.0 / 2013-02-27

* `ministamp` tag omits fingerprint in development mode
* Clarify documentation
* Comply with (Gemnasium) conventions for changelogs. Pull Request #1
  by Teemu Matilainen (@tmatilai).
* Bug fix: do not bundle assets when nonrelated files change
* Bug fix: do not bundle assets twice upon startup

# 1.0.0 / 2013-02-15

* Add development mode, where `minibundle` block will copy each asset
  as-is to the destination directory
* Clarify documentation
* Increase test coverage

# 0.2.0 / 2012-12-15

* Escape the values of custom attributes given in `minibundle` block
* Add semicolons between each JavaScript asset in bundling
* Show error in page output if asset bundling command failed

# 0.1.0 / 2012-12-07

* Add `ministamp` tag and `minibundle` block for Jekyll
* First release
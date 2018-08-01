# Change Log for dash-components-suite
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).

## [0.3.0] - 2018-07-11
### Changed
- a `generate-python-classes` build step is added to build scripts in `package.json`.
- Components are now imported from .py class files in the `packageNameUnderscored` directory. 

## [0.2.11] - 2017-08-08
### Fixed
- Fix src location of demo HTML page
- Fixed demo parent component

## [0.2.10] - 2017-08-08
### Fixed
- Fix tests in default component
- Fixed contribution instructions

### Changed
- Made the example component more representative of actual Dash components with `setProps` usage
- Added an `input` to the example component

### Added
- Added a templated `usage.py` file for testing the component

## [0.2.9] - 2017-08-08
### Fixed
- Another fix to `builder run demo`

## [0.2.8] - 2017-08-07
### Fixed
- Partial fix to `builder run demo`

## [0.2.7] - 2017-06-03
## Fixed
- Removed dependency on outdated `dash.ly` package

## [0.2.6] - 2017-03-10
## Added 
- Include new test package

## [0.2.5] - 2017-03-10
## Fixed
- The python code uses the new version of `dash` component loader

## Added
- The version number is now available in the module

## [0.2.4] - 2017-02-15
## Changed
- Moved React and React-DOM to external dependencies. This allows multiple component packages to use the same (externally loaded) React bundle.

## [0.2.3] - 2017-02-03
### Changed
- Change demo content-base to `demo/`
- Change demo server to localhost:9000 to resolve conflict with Dash server
- Add CHANGELOG to `builder-init` boilerplate

## [0.1.5] - 2016-07-12
### Added
- Script `publish-pypi` for publishing to PyPi
- `builder run demo` for running demo server on localhost:8080

## [0.1.4] - 2016-06-30
### Added
- Python package boilerplate to init/

## 0.1.0 - 2016-06-22
- Initial release


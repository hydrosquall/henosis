# Changelog
All notable changes to Henosis will be documented in this Changelog.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## 0.0.10 - 2018-04-27
### Fixed
- A small unintended KeyError introduced when logging requests after the 0.0.9 update.

## 0.0.9 - 2018-04-27
### Added
- A check that creates a temporary directory needed when storing models or
tagging functions.
- Additional fields for the response from the /requestlog API endpoint,
providing a "modelsUsed" field and a "modelsWithheld" field. When *predict_probabilities*
is set to True in your configuration file, these fields provide context behind how
frequently models meet their minimum recommendation (confidence) threshold.
- Additional checks for errors in making predictions.

### Changed
- The default model field return when requesting the API for recommendations. Changed
from *modelsQueried* to *modelsUsed*.

### Fixed
- A deprecation warning related to the WSGI import from gevent.

## 0.0.8 - 2018-04-12
### Fixed
- An issue with relative imports across Henosis files, changed to absolute imports.

## 0.0.7 - 2018-04-12
### Added
- Added the ability to set a minimum confidence threshold that dictates when
individual models will provide recommendations, which can be useful in certain
use cases.
- Added in a timer that periodically reloads models in memory if *preload_pickles* is
set to **True** and a float or integer value (in minutes) is specified in the
instance's configuration file.
- Added a check to ensure that only models in the *pickle_jar* are checked for use
if *preload_pickles* is set to True. This ensures no error is encountered if a model
has been deployed but isn't yet in the *pickle_jar*.
- Included additional logging for improved system monitoring and debugging.

### Changed
- Restructured Henosis such that server deployment and modeling classes are separated
and can be imported into a Python script or application with different imports. This
allows for easier use of Henosis by users and for better code maintainability.
*Breaks previous functionality.*

### Fixed
- An issue that was causing an error when using scikit-learn's TfidfVectorizer.

### Removed
- Removed pymssql requirement and functionality.

## 0.0.6 - 2018-03-15
### Fixed
- An issue where all X and y data (not only X_train and y_train) were resampled when upsampling or downsampling, causing
the test or validation set information to bleed into the training data.

## 0.0.5 - 2018-03-01
### Fixed
- A KeyError issue that prevented request logs to be stored in certain scenarios.

## 0.0.4 - 2018-02-27
### Configured
- Cross-origin request configuration and cleanup of code base.

## 0.0.3 - 2018-02-26
### Configured
- Cross-origin request configuration.

## 0.0.2 - 2018-02-26
### Added
- Addition of Flask-CORS to allow for cross-origin requests.

## 0.0.1 - 2018-02-23
### Added
- Initial release of Henosis codebase on PyPi.
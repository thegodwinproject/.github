# The Fallback .github for Gobuffalo

The default files for all gobuffalo projects.

## Community Standards

* LICENSE - MIT License

## Workflows

### Reusable Workflows

The reusable workflows are shared workflows can be called from the other
workflow that is configured for each project.

#### Standard Go Test

The standard go test, `go-test.yml`, will run configured `go test` command
for caller package on pre-configured environments.
Currently, the test will run on the latest version of Ubuntu, MacOS, and
Windows OSes with supported go versions.
Current supported go versions are 1.16 and 1.17. 1.18 support will be added
soon. (1.16 support will be deprecated once 1.18 support is added.)

#### Standard Go Coverage

The standard go coverage, `go-coverage.yml`, will run coverage test on the
latest version of Ubuntu with the latest supported version of go (currently
1.17), and will report the result to Code Climate, Coveralls, and Codecov.

### Starter Workflows

The starter workflows are a kind of workflow templates which could be used
for a new project when configuring a test workflow.

#### Standard Go Test for Gobuffalo

The test-only workflow for Go packages.

This starter workflow can be used when configuring a new test. It calls
reusable workflow "Standard Go Test" (`go-test.yml`) to run tests on supported
platforms with supported go versions.

#### Extended Go Test for Gobuffalo

The extended testing workflow for Go packages. (standard test + test coverage)

This starter workflow can be used when configuring a new test that supports
coverage reporting. It calls reusable workflow "Standard Go Test"
(`go-test.yml`) to run tests on supported platforms with supported go versions,
then calls another reusable workflow "Standard Go Coverage" (`go-coverage.yml`)
to run a coverage test on the latest version of Ubuntu with the latest
supported version of go.

To use this test, the caller project should have a `secret` named
`CC_TEST_REPORTER_ID` (Code Climate's reporter ID) then the secret will be
automatically passed to the called workflow and will be used when reusable
workflow runs coverage report.


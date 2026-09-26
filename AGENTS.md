# Repository guide

## Layout and setup

`lib/exception_notification/` contains notifier integrations; `lib/exception_notifier/` contains email-related code; `test/` contains tests and a dummy Rails application. `Appraisals` and `gemfiles/` describe compatibility combinations; `examples/` documents integrations. Follow `CONTRIBUTING.md`, including regression tests for behavior fixes and whitespace checks.

Install with `bundle install`, preserving `Gemfile.lock`. The gem declares Ruby >= 1.9.3 and historical Rails/notifier dependencies; use the relevant Appraisal combination rather than assuming a modern environment is compatible. SQLite/native dependencies are needed by the dummy app.

`bundle exec rake` first runs `setup_dummy_app`, which installs dependencies and migrates/prepares the dummy SQLite database, then runs the tests. With the fixture already prepared, `bundle exec rake test` runs the suite; `bundle exec rake test TEST=test/path_test.rb` narrows it. Confirm the dummy configuration points only at disposable local data. `test/test_helper.rb` loads Coveralls when available; account for outbound coverage reporting in an offline test setup. No separate lint command is defined.

## Completion and boundaries

Preserve unrelated edits after checking `git status --short`. Complete authorized local work through validation and repair; follow the contribution requirement to run all tests before claiming PR readiness. Use mocked notifier transports and synthetic exception data. Sending email/chat notifications, using real integration credentials, modifying external accounts, and gem publication require explicit authorization.

For documentation-only work, no new tests are required by the contribution guide; inspect links/commands and run `git diff --check`. Report exact dependency, dummy-app, or service blockers and continue independent work. Close with changed paths, checks actually run, and any unverified notifier delivery.

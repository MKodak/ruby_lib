# Changelogs
Commit based release not is [release_notes.md](./release_notes.md)

Release tags are https://github.com/appium/ruby_lib/releases .

## v9.6.0
### 1. Enhancements
- Reduce Global Driver
    - We need to provide `driver` to work `TouchAction` and `MultiAction` without global driver
        - `TouchAction`
            ```ruby
            driver =  Appium::Driver.new(opts, false).start_driver
            action = TouchAction.new.press(x: 45, y: 100).wait(5).release
            action.perform(driver)
            action = TouchAction.new.swipe(....)
            action.perform(driver)
            ```

        - `MultiAction`
            ```ruby
            driver =  Appium::Driver.new(opts, false).start_driver
            pinch 200, true, driver
            ```
- Add example to run multiple iOS Simulators [doc](https://github.com/appium/ruby_lib/blob/master/docs/ios_xcuitest.md#run-tests-on-multiple-simulators-with-xcode-9)
    - Require Xcode 9 and Appium 1.6.6

### 2. Bug fixes
- `scroll_to` is failed on some Android 5.0 and 5.1 devices
    - https://github.com/appium/ruby_lib/pull/638

### 3. Deprecations

### Special Thanks
- Fixing `acroll_to`
    - [@emen](https://github.com/emen)
- Add alias `quit_driver`
    - [@DylanLacey ](https://github.com/DylanLacey)

## v9.5.0
### 1. Enhancements
- Support `selenium-webdriver3.4.1+`
    - Support new `createSession`

### 2. Bug fixes

### 3. Deprecations
- Drop `selenium-webdriver` `3.0 ~ 3.4.0` since some methods depends on `selenium-webdriver3.4.1+`

## v9.4.10
### 1. Enhancements
- some refactoring
- add some documentations

### 2. Bug fixes

### 3. Deprecations

## v9.4.9
### 1. Enhancements

### 2. Bug fixes
- fix handling a tap gesture in xcuitest [#611](https://github.com/appium/ruby_lib/pull/611)

### 3. Deprecations

## v9.4.8
### 1. Enhancements
- within_context swallowing block return value [#311](https://github.com/appium/ruby_lib/issues/311)
- get current_package for Android [#604](https://github.com/appium/ruby_lib/issues/604)
- Show visibility on iOS page command [#609](https://github.com/appium/ruby_lib/pull/609)
    - related: allow showing all elements on ios page command [#310](https://github.com/appium/ruby_lib/issues/310)

### 2. Bug fixes

### 3. Deprecations
- Android: mark deprecated for client side xpath strategy [#608](https://github.com/appium/ruby_lib/pull/608)
- iOS: get_page method [#609](https://github.com/appium/ruby_lib/pull/609)

## v9.4.7
### 1. Enhancements

### 2. Bug fixes
- fix raise 500 error by `driver.remote_status` in `appium_server_version` [#599](https://github.com/appium/ruby_lib/issues/599)

### 3. Deprecations

## v9.4.6
### 1. Enhancements

### 2. Bug fixes
- reduce gemfile size [#591](https://github.com/appium/ruby_lib/issues/591)
    - Exclude `ios_tests`, `android_tests` and `grid` from gem

### 3. Deprecations

## v9.4.5
### 1. Enhancements
- add `touch_and_hols` for `mobile:` command in XCUITest [#581](https://github.com/appium/ruby_lib/pull/581)
- Driver disables Pry pager without asking [#582](https://github.com/appium/ruby_lib/issues/582)
- add grid environments in this repository.

### 2. Bug fixes

### 3. Deprecations

## v9.4.4
### 1. Enhancements
- add mobile gesture, `mobile: alert`
    - Required over https://github.com/appium/appium-xcuitest-driver/releases/tag/v2.28.6
- add travis example for ios [#573](https://github.com/appium/ruby_lib/pull/573)
- remove some redundant code [#572](https://github.com/appium/ruby_lib/pull/572), [#571](https://github.com/appium/ruby_lib/pull/571)
- update api-demos [#569](https://github.com/appium/ruby_lib/issues/569)

### 2. Bug fixes

### 3. Deprecations

## v9.4.3
### 1. Enhancements
- Use uiautomator for uiautomator2 [#561](https://github.com/appium/ruby_lib/pull/561)
    - improve stability for some methods
- don't use selenium-webdriver 3.5+ [#559](https://github.com/appium/ruby_lib/pull/559)
- Auto link bug # from release notes [#239](https://github.com/appium/ruby_lib/issues/239)

### 2. Bug fixes

### 3. Deprecations

### Special Thanks
- Thanks for checking uiautomator2
    - [@Edouard-chin](https://github.com/Edouard-chin), [@rajdeepv](https://github.com/rajdeepv)

## v9.4.2
### 1. Enhancements

### 2. Bug fixes
- fix drag_from_to_for_duration gets server error [#552](https://github.com/appium/ruby_lib/issues/552)

### 3. Deprecations

## v9.4.1
### 1. Enhancements

### 2. Bug fixes
- fix 9.4.0 release sudden failures [#546](https://github.com/appium/ruby_lib/issues/546)
    - XPath strategy for find_element/s sudden fail than uiautomator strategy.
    - Use `:xpath` strategy only for uiautomator2

### 3. Deprecations

## v9.4.0
### 1. Enhancements
- update mobile gesture APIs for XCUITest(WDA) [#514](https://github.com/appium/ruby_lib/pull/514)
    - For XCUITest(WebDriverAgent)
    - Users can call some [`mobile:` methods](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/ios-xctest-mobile-gestures.md) without `execute_script('mobile: tap', args)`.
    - Users can write test code without `.ref` method for elements in `execute_script`.
    - Example: https://github.com/appium/ruby_lib/pull/537
- Support UIAutomator2 strategy for Android[#505](https://github.com/appium/ruby_lib/issues/505)
    - Fix some find elemenet methods[#544](https://github.com/appium/ruby_lib/pull/544)

### 2. Bug fixes

### 3. Deprecations

## v9.3.8
### 1. Enhancements
- allow using TestObject server [#538](https://github.com/appium/ruby_lib/pull/538)

### 2. Bug fixes

### 3. Deprecations

## v9.3.7
### 1. Enhancements
- Remove appium suffix from find element [#532](https://github.com/appium/ruby_lib/pull/532)
    - rename `@driver.find_element/s_with_appium` to `@driver.find_element/s`
- fix documentations

### 2. Bug fixes

### 3. Deprecations
- `@driver.find_element/s_with_appium`
    - use `@driver.find_element/s` instead

## v9.3.6
### 1. Enhancements
- Add toggle touch id enrollment [#521](https://github.com/appium/ruby_lib/pull/521)

### 2. Bug fixes

### 3. Deprecations

## v9.3.5
### 1. Enhancements
- add some commands for Android and class chain for iOS [#513](https://github.com/appium/ruby_lib/issues/513)
    - iOS
        - `find_element :class_chain, 'XCUIElementTypeWindow/*/*/XCUIElementTypeStaticText'`
    - Android
        - `get_system_bars`
        - `get_display_density`
        - `is_keyboard_shown`
- add scrollable index parameter into scroll methods [#506](https://github.com/appium/ruby_lib/issues/506)
    - `scroll_to(text, scrollable_index = 0)`
    - `scroll_to_exact(text, scrollable_index = 0)`
- clear `@actions` in Appium::TouchAction if `perform` is called [#511](https://github.com/appium/ruby_lib/issues/511)

### 2. Bug fixes

### 3. Deprecations

## v9.3.4
### 1. Enhancements
- [remove workaround](https://github.com/appium/ruby_lib/pull/474/commits/57cc95264e83e14862f729683b93c1f020a30ce5) to pass CI
- document uiautomator events logging command [#319](https://github.com/appium/ruby_lib/issues/319)
- use predicate for XCUITest to improve performance [#493](https://github.com/appium/ruby_lib/issues/493)
    - `text/s`, `button/s`, `textfield/s`, `tags_exact`, `tags_include`
    - new: `find_ele/s_by_predicate`, `find_ele/s_by_predicate_include`

### 2. Bug fixes

### 3. Deprecations


## v9.3.3
### 1. Enhancements
- add tags_include/tags_exact to be able to find elements of arbitrary classes such as XCUIElementTypeTextView [#488](https://github.com/appium/ruby_lib/issues/488)

### 2. Bug fixes

### 3. Deprecations

## v9.3.2
### 1. Enhancements
- allow SAUCE_ENDPOINT env var to override sauce server url/path [#485](https://github.com/appium/ruby_lib/pull/485)
    - Read [readme](https://github.com/appium/ruby_lib/blob/89c7c89be058153d119d517eab22ccc318d33649/readme.md#sauce-labs-env-vars)'s `SAUCE_ENDPOINT` section.

### 2. Bug fixes

### 3. Deprecations

## v9.3.1
### 1. Enhancements
- Clarify disabling Sauce Labs. [#471](https://github.com/appium/ruby_lib/pull/471)
- add getting performance [#479](https://github.com/appium/ruby_lib/issues/479)
    - **require appium-base-driver@2.1.7**

### 2. Bug fixes
- Fix missed var rename [#481](https://github.com/appium/ruby_lib/pull/481)

### 3. Deprecations

## v9.3.0
### 1. Enhancements
- wait / wait_true need global defaults [#250](https://github.com/appium/ruby_lib/issues/250)
    - You can set default value in `appium_lib`
    - e.g.: [lib/appium_lib/driver.rb](https://github.com/appium/ruby_lib/blob/34803ef6b7b94df9ef4e147ba8fec5c1d2cfaada/lib/appium_lib/driver.rb#L341-L351)
- Problem with delta_x/delta_y in swipe method [#461](https://github.com/appium/ruby_lib/issues/461)
    - Revert _fix arguments for `move_to` in `swipe` method._ in Appium v8.2.1
    - `delta_x/delta_y` replace to `offset_*` for iOS
        - e.g.: `swipe start_x: start_x, start_y: start_y, end_offset_x: 0, offset_y: -100`
    - `delta_x/delta_y` replace to `end_*` for Android
        - e.g.: `swipe start_x: start_x, start_y: start_y, end_x: start_x, end_y: start_y - 100`
    - The reason why there are two kind of arguments is the following issue.
        - [Difference behaviour between iOS and Android regarding with `swipe` action #7702](https://github.com/appium/appium/issues/7702)
- Clarify disabling Sauce Labs. #471
  - update documentations

### 2. Bug fixes
- REQUIRED_VERSION_XCUITEST [#463](https://github.com/appium/ruby_lib/issues/463)
- find elements except for name attributes in text/s, button/s [#462](https://github.com/appium/ruby_lib/issues/462)
    - Return only **visible** elements
        - Previously, these methods return **all** elements.

### 3. Deprecations
- Problem with delta_x/delta_y in swipe method [#461](https://github.com/appium/ruby_lib/issues/461)
    - `delta_x/delta_y` are replaced to `offset_*` for iOS and `end_*` for Android.

## v9.2.0
### 1. Enhancements
- update set_wait / no_wait logic #249
    - `no_wait` just set `implicit_wait = 0`
    - `set_wait` just set `@default_wait` or arbitrary time as `implicit_wait`
    - remove `last_waits` attribute

### 2. Bug fixes
- automationName always nil if set automationName in server side #450

### 3. Deprecations

## v9.1.3

Support selenium-webdriver 3.0.4+

### 1. Enhancements
- Improve performance for button/s and text/s #442
- Should use `open_timeout` or `read_timeout` instead of `timeout` #436
- add documentation for alternative long_press method #440

### 2. Bug fixes

### 3. Deprecations

## v9.1.2
### 1. Enhancements
- add `appium_client_version`: https://github.com/appium/ruby_lib/issues/260
- add some tests and fix some rubocop syntax errors

### 2. Bug fixes
- fix `set_immediate_value`: https://github.com/appium/ruby_lib/issues/263

### 3. Deprecations

## v9.1.1
### 1. Enhancements

### 2. Bug fixes
- fix Finds exact in ios does not return an array #423

### 3. Deprecations

Thanks @slipy12

## v9.1.0
### 1. Enhancements
- update dependencies
    - Support selenium-webdriver 3.0.2+
        - If you'd like to use `selenium-webdriver2.x`, please use `appium_lib9.0.0`

### 2. Bug fixes

### 3. Deprecations
- Drop Ruby 1.9.3, 2.0, 2.1 support
    - Because these ruby versions have already stop updating.

## v9.0.0
### 1. Enhancements
- Support `XCUITest` strategy for iOS
    - Basically, `XCUITest` strategy is compatible with `Appium` strategy in this library.
    - But users who use XPath should be check [this document](https://github.com/appium/ruby_lib/blob/master/docs/ios_xcuitest.md) since XPath has performance issue
        - Users who use `find_element/s` should work fine.
        - tests for elements are [here](https://github.com/appium/ruby_lib/tree/master/ios_tests/lib/ios/specs/ios/element)

Special thanks to @montdidier

### 2. Bug fixes

### 3. Deprecations


## v8.2.1
- fix arguments for `move_to` in `swipe` method.
    - https://github.com/appium/ruby_lib/pull/405
    - Please set `:delta_x` and `:delta_y` as the distance from start to move.

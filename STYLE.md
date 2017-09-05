# The sensei Developer's Style Guide

## Code Conventions

All names and comments *MUST* be written in English.

### Naming

The following naming conventions *MUST* be used:

|Construct|Convention|
|---------|----------|
|module|`lower-dash-case`|
|module exporting default class|`UpperCamelCase`|
|all other modules|`lowerCamelCase`|
|classes, interfaces, and type aliases|`UpperCamelCase`|
|enums and enum value names|`UpperCamelCase`|
|constants|`UPPER_CASE_WITH_UNDERSCORES`|
|variables|`lowerCamelCase` or `_lowerCamelCase`*|
|parameters|`lowerCamelCase` or `_lowerCamelCase`*|
|public properties|`lowerCamelCase`|
|protected/private properties|`_lowerCamelCase`|

*: Variables and parameter names generally *SHOULD NOT* be prefixed with underscores, but this may be
  warranted in rare cases where two variables in nested scopes make sense to have the same name, while avoiding shadowing the outer variable.

The following naming conventions *SHOULD* be used:

|Variable type|Convention|
|-------------|----------|
|Deferred|`dfd`|
|Promise|`promise`|
|Coroutine|`co`|
|Identifier|`id`|
|Numeric iterator|`i`, `j`, `k`, `l`|
|String iterator (for-in)|`key`, `k`|
|Unused iterator\|value (for-in)|`_`|
|Context as first argument|`self`|
|Configuration object|`config`|
|Destroyable handle|`handle`|
|Error object|`error`|
|Event|`event`|
|Options arguments|`options`|
|Origin, source, from|`source`|
|Destination, target, to|`target`|
|Variable arguments collection {...}|`args`|
|Coordinates|`x`, `y`, `z`, `width`, `height`, `depth`|
|All others|Do not abbreviate|

1. All names *SHOULD* be as clear as necessary, *SHOULD NOT* be contracted just for
    the sake of less typing, and *MUST* avoid unclear shortenings and
    contractions (e.g. `MouseEventHandler`, not `MseEvtHdlr` or `hdl` or `h`).
1. Names *SHOULD* use American English (`en-us`) spelling.
1. Names representing an interface *MUST NOT* use "I" as a prefix
  (e.g. `Event` not `IEvent`).
1. Abbreviations and acronyms *SHOULD NOT* be uppercase when used as a name
  (e.g. `getXml` not `getXML`).
1. Collections *SHOULD* be named using a plural form.
1. Names representing boolean states *SHOULD* start with `is`, `has`, `can`, or `should`.
1. Names representing boolean states *SHOULD NOT* be negative
  (e.g. `isNotFoo` is unacceptable).
1. Names representing a count of a number of objects *SHOULD* start with `num`.
1. Names representing methods *SHOULD* be verbs or verb phrases
  (e.g. `getValue()`, not `value()`).
1. Factories or non-constructor methods that generate new objects *SHOULD* use the verb
   "create".
1. Magic numbers *MUST* either be represented using a constant or enum, or be prefixed
  with a comment representing the literal value of the number
  (e.g.
  `if (event.keyCode === Keys.KEY_A)`
  or
  `if (event.keyCode === /* "a" */ 97)`
  )

### Variables

1. All variable declarations *SHOULD* use one `local` declaration per
    variable. The exception to this rule is when capturing multiple returns.
    This prevents variable declarations being lost inside long lists that may
    also include immediate assignments:

    ```lua
    // correct

    local items = getItems()
    local length = #items
    local i = 0
    local item

    // also right

    local items = getItems()
    for i, item in ipairs(items) do

    // incorrect

    local items, length = getItems(), #items.length
    local i, item = 0
    ```

1. Variable declarations *SHOULD* be grouped by assignment of data type
   in the following order:
    * i. `function calls | declaraions`
    * ii. `non-function data types`
    * iii. `instantiation without immediate assignment`

    ```lua
    // correct

    local items = getItems()
    local length = #items
    local i = 0
    local item

    // incorrect

    local items = getItems()
    local item
    local length = #items
    local i = 0
    ```

1. Variables *SHOULD* be declared where they are first assigned:

    ```lua
    // correct

    local Renderer = {}
    
    function Renderer:render ()
        local items = self.getItems()

        if not #items then
            return
        end

        for i, item in ipairs(items) do
            self.renderItem(item)
        end
    end

    // incorrect

    local Renderer = {}
    
    function Renderer:render ()
        local items = this.getItems()
        local i
        local item

        if not #items.length then
            return
        end

        for i, item in ipairs(items) do
            self.renderItem(item)
        end
    end
    ```

1. The most appropriate data types *SHOULD* be used in all cases (e.g. boolean for
    booleans, not number).

### Coding Conventions

#### General

1. Strings *MUST* use single quotes.
   `local sampleText = 'a string of text'`
   `local value = object['keyNameString']`
   
*...to be continued.*

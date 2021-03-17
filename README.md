# Awesome-Xcode-Options
A list of Xcode launch arguments, environment variables and command line options that help with debugging tasks.

## Launch arguments

### Localization

- `-NSDoubleLocalizedStrings YES`: double the length of all localized strings to see how longer languages will affect UI/layout
- `-NSShowNonLocalizedStrings YES`: uppercase all nonlocaized strings
- `-AppleLanguages (es)`: can either be the name of the language (“Spanish”), or its language code (es), but since localization files are keyed by their ISO 639 code, using the code is preferable to the actual name of the language

### Core Data

- `-com.apple.CoreData.SQLDebug 3`: takes a value between 1 and 3, with increasing verbosity
- `-com.apple.CoreData.SyntaxColoredLogging YES`
- `-com.apple.CoreData.MigrationDebug`

## Environment variables

### Zombies

- `NSZombieEnabled`
- `NSDeallocateZombies`: actually free the memory of zombie objects, as opposed to secretly retaining them for reporting

### Allocations

- `MallocScribble
- `MallocGuardEdges`
- `MallocStackLogging`
- `MallocStackLoggingNoCompact`

### I/O Buffering

- `NSUnbufferedIO`: don't buffer logging to stdout (sterr is unbuffered by default)

### `dyld`

- `DYLD_FRAMEWORK_PATH`
- `DYLD_FALLBACK_FRAMEWORK_PATH`
- `DYLD_VERSIONED_FRAMEWORK_PATH`
- `DYLD_LIBRARY_PATH`
- `DYLD_FALLBACK_LIBRARY_PATH`
- `DYLD_VERSIONED_LIBRARY_PATH`
- `DYLD_PRINT_TO_FILE`
- `DYLD_SHARED_REGION`
- `DYLD_INSERT_LIBRARIES`
- `DYLD_FORCE_FLAT_NAMESPACE`
- `DYLD_IMAGE_SUFFIX`
- `DYLD_PRINT_OPTS` (macOS 10.4+)
- `DYLD_PRINT_ENV` (macOS 10.4+)
- `DYLD_PRINT_LIBRARIES`
- `DYLD_BIND_AT_LAUNCH`
- `DYLD_DISABLE_DOFS`
- `DYLD_PRINT_APIS` (macOS 10.4+)
- `DYLD_PRINT_BINDINGS` (macOS 10.4+)
- `DYLD_PRINT_INITIALIZERS` (macOS 10.4+)
- `DYLD_PRINT_REBASINGS`
- `DYLD_PRINT_SEGMENTS` (macOS 10.4+)
- `DYLD_PRINT_STATISTICS` (macOS 10.4+)
- `DYLD_PRINT_DOFS`
- `DYLD_PRINT_RPATHS`
- `DYLD_SHARED_CACHE_DIR`
- `DYLD_SHARED_CACHE_DONT_VALIDATE`
- `DYLD_ROOT_PATH` and `DYLD_PATHS_ROOT` appear to be synonyms and allow you to reset the "root" for searching for libraries/frameworks/etc. This is available on macOS/iPhoneSimulator but not iOS.
- `DYLD_DISABLE_PREFETCH` disables the pre-fetching of the content of `__DATA` and `__LINKEDIT` segments.
- `DYLD_PRINT_LIBRARIES_POST_LAUNCH` is the same as `DYLD_PRINT_LIBRARIES` but prints them right after launch has finished.
- `DYLD_NEW_LOCAL_SHARED_REGIONS` and `DYLD_NO_FIX_PREBINDING` are ignored and don't do anything anymore.
- `DYLD_PREBIND_DEBUG` prints out debug information on why prebinding was not used.
- `DYLD_PRINT_TO_STDERR` only applies to iOS and forces output to stderr (instead of stdout) to help it show up on console logs.
- `DYLD_PRINT_WEAK_BINDINGS` prints debug information on weak bindings.
- `DYLD_PRINT_WARNINGS` prints a bunch of warnings (mostly regards to closures and how they are being used).
- `DYLD_PRINT_CS_NOTIFICATIONS` prints information about the core symbolicator.
- `DYLD_PRINT_INTERPOSING` prints details about interposes that occur.
- `DYLD_PRINT_CODE_SIGNATURES` prints details about code signatures (specifically successes and failures).
- `DYLD_USE_CLOSURES` is a dyld3 feature, but doesn't appear to work for anybody non-internal (need `CSR_ALLOW_APPLE_INTERNAL` set).
- `DYLD_IGNORE_PREBINDING` has three values (`all`, `app` and `nonsplit`) with `nonsplit` being the default if a value is not supplied.
- `DYLD_SKIP_MAIN` is an apple only feature used for testing dyld (need `CSR_ALLOW_APPLE_INTERNAL` set).

## `xcodebuild -X` options

- **TODO**

## References

- https://nshipster.com/launch-arguments-and-environment-variables/
- https://stackoverflow.com/a/51504440/4789448 for some `dyld` environment variables
- https://developer.apple.com/library/archive/technotes/tn2239/_index.html
- `man dyld`, which can be read for those environment variables lacking descriptions

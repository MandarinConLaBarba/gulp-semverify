# Semverify

Used to warn when your package dependencies don't match your semver policy. Helps w/ enforcing a particular dependency version policy.

## Usage

Determine what your policy is (e.g. X.Y.*, where you will only get new patch-level versions). Then add gulp task below to make sure there are no violations:

```
gulp.task('semver-policy', function() {

    gulp.src(__dirname + "/*.json")
        .pipe(semverify({policy : "X.Y.Z"}));
});


```

If there are any issues you should get an error:

```
[12:55:21] Starting 'semver-policy'...
[12:55:21] Finished 'semver-policy' after 6.06 ms
[12:55:21] Violation found in dependency: event-stream - The ^ operator was found but the policy doesn't include it.
[12:55:21] Violation found in dependency: underscore - The ^ operator was found but the policy doesn't include it.

events.js:72
        throw er; // Unhandled 'error' event
              ^
Error in plugin 'gulp-semverify'
There were policy violations with one or more of your dependencies.
```

See [semverify](https://github.com/MandarinConLaBarba/semverify) for gulp integration.
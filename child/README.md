nebula-release-plugin-bug example
====================================

# Problem

In some java version greater than 1.8 (1.14 is known to have this problem) Grgit's

    Grgit.open(dir: gitRoot)

fails if gitRoot is a string and does so so badly that none of the release tasks are created.

#Example

In gradle.properties git.root=..

## Old and Broken

Run

    ./gradlew devSnapshot

Build fails

## New Hotness

Run

    ./gradlew devSnapshot -Prelease.workCorrectly=true

Hack applied to git root before release plugin applied.  Build succeeds.

# Conclusion

nebula-release-plugin needs to convert the git.root to a file via project.file prior to passing it to Grgit.


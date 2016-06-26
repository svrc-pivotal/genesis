# Improvements

- Genesis now supports the Genesis Index, a free service available
  online at https://genesis.starkandwayne.com that tracks releases
  and stemcells from bosh.io and Github.  Genesis now uses this to
  supply version, tarball URL and SHA1 checksum information for
  both releases and stemcells.

  This makes it possible for newer BOSH CLIs to transparently
  upload missing releases and stemcells to your BOSH director,
  which in turn enables Concourse pipelines to easily roll
  stemcell and release upgrades through unattended.

  One side-effect of this change is that the "latest" version
  keyword now no longer means "latest available on the BOSH
  director", but instead "latest known to the index".

  The public Genesis Index is automated and watches Github and
  bosh.io for new releases and stemcells, so that it stays
  up-to-date.  Sites wishing to run a local Genesis Index may
  easily do so by pushing the [genesis-index][index] app to their
  Cloud Foundry instance.

- `genesis use stemcell` now defaults to 'latest' version,
  just like `genesis add release`.  Fixes #36

- `genesis new environment` now defaults to the current site if no
  site name is given.  Fixes #28

- Templated site creation now provides similar output to normal
  site creation (including the `tree` output).  Fixes #29

# Bug Fixes

- Fix typo in environment teardown messaging.

- Argument processing got an overhaul, to make it more difficult
  to supply (unused and previously ignored) command-line flags.
  Now, genesis will print errors for unrecognized options.
  Fixes #15

[index]: https://github.com/starkandwayne/genesis-index
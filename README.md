# Systjik — retired

This repository is retired as of 1 November 2026. It is retained as a historical
source checkpoint and is no longer maintained or used for fleet deployment.

Use the maintained projects:

- [Dotjik system policy](https://github.com/tijptjik/dotfiles/tree/main/system)
  for system configuration, host manifests and operational documentation.
- [Dotjik workflows](https://github.com/tijptjik/dotfiles/blob/main/docs/tjikup.md)
  for home and system deployment and maintenance recipes.
- [Tjikup in tjikOS](https://github.com/tijptjik/tjikos/tree/main/apps/tjikup)
  for the native runner and `systjik` command implementation.
- [Synctjik in tjikOS](https://github.com/tijptjik/tjikos/tree/main/apps/synctjik)
  for backup and recovery engines.

Do not run this checkout's `setup.sh`, Chezetc hooks or migration recipes against
live machines. Use the current Dotjik
[bootstrap](https://github.com/tijptjik/dotfiles/blob/main/system/SERVER-BOOTSTRAP.md)
and [rebuild](https://github.com/tijptjik/dotfiles/blob/main/system/SERVER-REBUILD.md)
guides instead. Direct fixes and new work to the maintained repositories above.

The retained files include an intermediate migration checkpoint, not a supported
deployment release. Repository retirement does not certify that every host has
completed its backup, restore or deployment acceptance gates. Keep host recovery
material until those checks pass.

The historical validation suite requires legacy tools, including Chezmoi. At
retirement, Bash and Fish syntax checks passed; 97 tests ran with two errors due
to missing Chezmoi and six skips. Live template rendering was also skipped.
No fleet deployment was performed as part of retirement.

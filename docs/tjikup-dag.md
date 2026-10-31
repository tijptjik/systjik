> **Retired repository:** this document is historical and is not an active
> deployment guide. See the [retirement notice](../README.md) for maintained replacements.

# System recipe graph

System maintenance is declared in `tjikup/recipes.json` and scheduled by the
Rust tjikup runner. See [Tjikup recipes](tjikup.md). Templates live in
`etc/.chezmoitemplates/tjikup`, outside the hook inventory. The system file pass
uses the managed Chezetc wrapper, and rendered commands explicitly use
noninteractive sudo with a small environment allowlist. Resource names are shared
with home recipes. Final networking and release tasks wait for both layers.

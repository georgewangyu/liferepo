# Private Repo Pointer Contract

This repo is public and must not hardcode one person's private-repo name or
absolute filesystem path.

## Naming and Docs Rule

- In public docs, refer to private state as `<private-repo>`.
- Do not write personal absolute filesystem paths in public specs.

## Runtime Resolution Order

Tools should resolve private repo root in this order:

1. `LIFEREPO_PRIVATE_ROOT` (preferred)
2. `PRIVATE_REPO_ROOT` (fallback)
3. `GEORGEREPO_ROOT` (legacy compatibility)
4. local pointer config in `liferepo/.liferepo/local/private_repo.json`
5. marker discovery via `.liferepo-private.json`

## Local Pointer Config (Not Committed)

Location:

```text
liferepo/.liferepo/local/private_repo.json
```

Example:

```json
{
  "private_repo_name": "my-private-repo"
}
```

`private_repo_path` is optional. If omitted, tools resolve the private repo as
`../<private_repo_name>` relative to `liferepo/`.

Path override example:

```json
{
  "private_repo_name": "my-private-repo",
  "private_repo_path": "../my-private-repo"
}
```

Bootstrap command (from `liferepo/`):

```bash
python3 ../georgeskills/scripts/bootstrap_private_repo.py --name my-private-repo --create
```

## Private Repo Marker

Private repo root should include:

```text
.liferepo-private.json
```

Example:

```json
{
  "schema_version": 1,
  "role": "liferepo-private-state"
}
```

This marker lets tools discover the right private state repo without relying on
a fixed folder name.

# Contributing

Contributions should improve this source-linked index without adding image files.

## What to include

Prefer original publisher repositories, official research archives and maintainer-authored test fixtures. A maintained derivative test fixture is acceptable when its provenance is disclosed and the link points to the maintainer of that derivative. Do not substitute a download mirror for an available original source.

Do not commit DICOM, NIfTI, ZIP study archives, screenshots containing patient information, vendor installers or credentials. Do not link to leaked, scraped, private or patient-identifiable clinic material. A site's public visibility alone is not evidence of consent or de-identification.

## Verify an entry

1. Search the web for the source, then open the actual source page. Search snippets alone are insufficient. Read the original README, data paper and terms where needed.
2. Record exactly which collection, version, folder or filenames the entry covers. Separate scanner manufacturer/model from viewing or reconstruction software. Do not infer a scanner from a viewer name.
3. Verify modality, format, vendor/model and transfer syntax where stated. Record missing details as `not stated`. Name the transfer syntax and UID when supported; do not infer either from a ZIP or gzip extension. Enhanced multi-frame is an object organization.
4. Record byte size or publisher units and the size's scope. If calculating from public repository metadata, record its immutable tree hash, file count and exclusion rules. Do not download image files just to measure them.
5. Quote the source's licence or terms name and link to the evidence. If absent, use exactly `terms not stated`. Distinguish repository/code licences from image permissions and retain upstream notices.
6. Check whether access requires registration, payment, credentialing, training, a data use agreement or individual approval. An open landing page does not prove open downloads. Use `null` for unresolved registration, explain it prominently, and do not claim a completed download.
7. Record the privacy basis: a synthetic or physical phantom, an averaged atlas, a publisher's de-identification statement or a documented public research release. For established decoder fixtures, describe the maintainer's provenance and any missing per-file evidence. Reject known identifiable material; never attempt to identify a subject.
8. Record the check date, actual search queries, opened URLs and access method. Do not mark an inaccessible source as verified. Put incomplete or inaccessible candidates in `candidates`, outside the main tables, with the reason.

Do not make a dataset appear verified merely by checking its homepage. Evidence must support the selected dataset. Do not broaden an entry from a checked subset to an entire mixed repository. If a source changes access or terms, update the entry or move it to the candidate list.

## Keep the two formats aligned

Update both [datasets.json](datasets.json) and [README.md](README.md). Use a stable, unique, lowercase hyphenated `id`; its README anchor should match. Count each selected dataset or fixture group once, even if several vendor or format lookups reference it.

The JSON uses:

- `schema_version`, `checked_on`, `index_license`, `verification_scope` and `counts` for catalogue metadata.
- `datasets` for opened, source-verified entries. Each has `id`, `title`, `category`, `modalities`, `format`, `source_url`, `content`, `vendors`, `transfer_syntax`, `size`, `licenses`, `access`, `privacy`, `notes` and `verification`.
- `category`: `dental_cbct`, `ct`, `mri`, `transfer_syntax` or `nifti`. A collection may list several modalities while having one primary category.
- `vendors[].role`: `scanner` or `software`. Empty `vendors` or `models` means not stated, not an inferred manufacturer.
- `transfer_syntax.status`: `stated`, `not_stated` or `not_applicable`; `values` contains objects with `name` and `uid`.
- `size.bytes`: integer or `null`; `basis` is `publisher`, `publisher_metadata`, `repository_manifest` or `not_stated`. Preserve approximate source units in `display`; do not invent exact bytes from rounded MB.
- `licenses[]`: source name, URL, scope and optional qualifications. The index licence never supplies a missing dataset licence.
- `access.registration_required`: `true`, `false` or `null` (unknown); `download_tested` must reflect what actually happened.
- `privacy`: evidence basis, description, source URL and whether an independent audit occurred. Do not claim auditing from a page review.
- `verification.status`: `source_verified`; `methods` lists the actual mechanisms used. `page_open` covers browser page access; `web_open`, `https_html` and `github_api` are more specific alternatives. `image_files_downloaded` remains false for index-only checks.
- Optional `files` identifies a selected fixture group using names, sizes and original source links.
- `coverage` maps requested vendors and formats to existing dataset IDs. Empty IDs preserve explicit gaps.
- `candidates` stores `unverified` or `excluded` sources, opening status, reasons and check evidence. Candidates are not included in dataset counts.

Validate JSON syntax locally:

```sh
python3 -m json.tool datasets.json > /dev/null
```

Also check unique IDs, working local anchors, count totals, coverage references and matching licence/access wording. For an update, report which pages you opened and which details remain uncertain. No image download or new automated test suite is needed for a text correction.

Contributions to the index text and original descriptions are under [CC BY 4.0](LICENSE). You must have permission to contribute your wording; linking an external dataset does not change its terms.


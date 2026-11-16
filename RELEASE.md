# 📦 Release and versioning process

## 1. Release readiness

A release should represent a coherent and reviewable state of the repository. Do not tag a release solely because documentation was added or a workflow ran.

Before release:
1. Review all changes since the previous release.
2. Confirm the README describes the current implementation.
3. Update the Unreleased section of the changelog.
4. Validate notebooks as JSON and inspect their saved outputs.
5. Run relevant deterministic tests.
6. Check frontend pages and local assets.
7. Review source access, privacy, and retention implications.
8. Confirm no credentials or unapproved datasets are included.
9. Document known defects and untested areas.

## 2. Versioning

If the project begins publishing tagged software releases, use semantic versioning where it fits the actual compatibility surface:
- major for incompatible public interface or schema changes;
- minor for backward-compatible capabilities;
- patch for compatible fixes.

Until a stable API or package exists, dated release notes may be more informative than implying a software compatibility contract.

## 3. Release notes

Include:
- concise summary;
- Added, Changed, Fixed, and Security sections where applicable;
- affected notebooks, frontend pages, or documentation;
- environment and compatibility notes;
- schema or methodology changes;
- validation commands and observed results;
- known limitations and data coverage.

## 4. Data and model releases

A release that includes an analytical dataset or model must also document its source permissions, collection window, schema, label provenance, preprocessing, evaluation split, metrics, and limitations. Do not bundle private raw review data by default.

## 5. Rollback

For a code or frontend regression, identify the last known-good commit or tag and revert the smallest safe change. For a secret or data exposure, rollback is not enough: revoke credentials, restrict access, identify copies, and follow the security incident process.

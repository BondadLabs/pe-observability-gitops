# Grafana Cloud Dashboards

This folder is the **source of truth** for the **Infrastructure** folder in Grafana Cloud, synced via [Grafana's Git Sync](https://grafana.com/docs/grafana/latest/dashboards/build-dashboards/manage-version-history/#git-sync) feature.

Any dashboard JSON file committed here is automatically reflected in the Infrastructure folder of Grafana Cloud. Likewise, dashboards saved in Grafana Cloud within that folder are pushed back to this repository.

## Structure

```
gc-dashboards/
├── README.md
├── kubevirt      # Grafana dashbaords for VMs
└── *.json        # Grafana dashboard JSON files
```

Each `.json` file represents one Grafana dashboard exported in the standard Grafana JSON model format.

## Workflow

### Making changes via Git (recommended)

1. Edit or add a dashboard `.json` file in this directory.
2. Commit and push to `main`.
3. Grafana Cloud picks up the change automatically via the git sync interval.

### Making changes via Grafana UI

1. Edit the dashboard in Grafana Cloud (Infrastructure folder).
2. Save the dashboard — Grafana commits the updated JSON back to this repo.
3. Pull the latest changes locally before making further edits.

## Adding a new dashboard

Export the dashboard JSON from Grafana (**Dashboard settings → JSON Model → Copy to clipboard** or **Share → Export**), save it as a descriptive kebab-case filename (e.g., `cluster-overview.json`), and commit it here.

## Naming conventions

| Convention | Example |
|---|---|
| Kebab-case filenames | `node-resource-usage.json` |
| Match the dashboard title | Title `"Node Resource Usage"` → `node-resource-usage.json` |

## Notes

- Do **not** manually edit the `"id"` or `"uid"` fields in JSON files — Grafana manages these.
- The git sync target branch is `main`. Changes on other branches are **not** synced.
- Folder path in Grafana Cloud: **Infrastructure**

# Development Notes

## Known Limitations

- The **transform and create product** functionality is intermittently unreliable. Root cause not yet identified.
- The code is optimized for CouchDB, but Kaleido does not expose a CouchDB config option, so those optimizations are not fully utilized in the managed deployment.

## IoT Sensor Endpoint

Currently not fully production-ready. It traverses the existing database and assigns sensor data to the sole Distributor identity in the demo setup. Scaling to multi-distributor production is straightforward but was not implemented without a dedicated IoT device.

## Kaleido-Specific Pitfalls

- **Never use `omitempty`** in Go structs - Kaleido's schema validation will reject these.
- **Protect the `.db` file** - it contains Kaleido network-specific credentials. Losing it requires rebuilding the Kaleido network from scratch before redeployment.

# Developer Cookbook — api-oss-hub
**Stack:** Python 3.11, SQLite, semver, AIOSS_FORMAT
**Domain:** Sovereign project registry: metadata, versioning, discovery for 123 Anticloud projects
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_hub import ProjectHub
hub = ProjectHub('./hub.db', aioss_chain='./hub.aioss')
hub.publish(project='K_BRAINFLOW', version='1.2.0', metadata={'domain':'biosignals','trl':8})
results = hub.search('HIPAA biosignal', pax_model='./pax-27b-q4.gguf')
for r in results: print(f'{r.project} v{r.version}: {r.score:.2f}')
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-hub output:
chain_hash = aioss_append("./api_oss_hub.aioss",
                           result_bytes, "api-oss-hub")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-hub operations are logged to api-oss-logging and audited by api-oss-compliance.

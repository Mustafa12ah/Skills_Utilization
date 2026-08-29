# Security Scan Report

**Scan date:** 2026-08-29 14:14:08
**Commit:** `ba9ec866c00358ab4f32592745f4aa58fcd3756c`
**Triggered by:** Mustafa12ah

---

## 1. Bandit — Python security issues

```
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager, possibly rendering your system unusable. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv. Use the --root-user-action option if you know what you are doing and want to suppress this warning.

[notice] A new release of pip is available: 25.0.1 -> 26.2.1
[notice] To update, run: pip install --upgrade pip
[main]	INFO	profile include tests: None
[main]	INFO	profile exclude tests: None
[main]	INFO	cli include tests: None
[main]	INFO	cli exclude tests: None
[main]	INFO	running on Python 3.12.14
Run started:2026-08-29 11:14:15.540703+00:00

Test results:
>> Issue: [B104:hardcoded_bind_all_interfaces] Possible binding to all interfaces.
   Severity: Medium   Confidence: Medium
   CWE: CWE-605 (https://cwe.mitre.org/data/definitions/605.html)
   More Info: https://bandit.readthedocs.io/en/1.9.4/plugins/b104_hardcoded_bind_all_interfaces.html
   Location: ./app.py:4:29
3	if __name__ == "__main__":
4	    app.run(debug=True, host="0.0.0.0", port=5000)

--------------------------------------------------

Code scanned:
	Total lines of code: 776
	Total lines skipped (#nosec): 0
	Total potential issues skipped due to specifically being disabled (e.g., #nosec BXXX): 0

Run metrics:
	Total issues (by severity):
		Undefined: 0
		Low: 0
		Medium: 1
		High: 0
	Total issues (by confidence):
		Undefined: 0
		Low: 0
		Medium: 1
		High: 0
Files skipped (0):
```

## 2. Hadolint — Dockerfile issues

```
Unable to find image 'hadolint/hadolint:latest' locally
latest: Pulling from hadolint/hadolint
83cf56c1bf8f: Pulling fs layer
83cf56c1bf8f: Download complete
83cf56c1bf8f: Pull complete
3c27a54fbbc3: Download complete
Digest: sha256:32dac94127fd60b7b7e3fbfc65e1383b9b5e25c9bfd7b8536de7a539fe68a12d
Status: Downloaded newer image for hadolint/hadolint:latest
-:10 DL3013 [1m[93mwarning[0m: Pin versions in pip. Instead of `pip install <package>` use `pip install <package>==<version>` or `pip install --requirement <requirements file>`
-:17 DL3066 [92minfo[0m: Non-numeric user-id may not be resolvable by host system
```

## 3. TruffleHog — exposed secrets

```
Unable to find image 'trufflesecurity/trufflehog:latest' locally
latest: Pulling from trufflesecurity/trufflehog
4f4fb700ef54: Pulling fs layer
4f4fb700ef54: Pulling fs layer
fbb7b6f067ab: Pulling fs layer
f7ee36c9aa34: Pulling fs layer
99855ed812e7: Pulling fs layer
4b6a87546921: Pulling fs layer
4f4fb700ef54: Already exists
4f4fb700ef54: Pull complete
f7ee36c9aa34: Download complete
f7ee36c9aa34: Pull complete
4b6a87546921: Download complete
fbb7b6f067ab: Download complete
fbb7b6f067ab: Pull complete
99855ed812e7: Download complete
4b6a87546921: Pull complete
99855ed812e7: Pull complete
Digest: sha256:deb2af10659a488a14d262a323addcde099d99827a1cf1dc4e93c17915c39f08
Status: Downloaded newer image for trufflesecurity/trufflehog:latest
🐷🔑🐷  TruffleHog. Unearth your secrets. 🐷🔑🐷

2026-08-29T11:14:23Z	info-0	trufflehog	running source	{"source_manager_worker_id": "MsBcz", "with_units": true}
Found unverified result 🐷🔑❓
Detector Type: Github
Decoder Type: BASE64
Raw result: ghs_15368_eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9
Rotation_guide: https://howtorotate.com/docs/tutorials/github/
Version: 2
File: /src/.git/config
Line: 12

2026-08-29T11:14:23Z	info-0	trufflehog	finished scanning	{"chunks": 135, "bytes": 367572, "verified_secrets": 0, "unverified_secrets": 1, "scan_duration": "304.25461ms", "trufflehog_version": "3.97.1", "verification_caching": {"Hits":0,"Misses":2,"HitsWasted":0,"AttemptsSaved":0,"VerificationTimeSpentMS":537}}
```

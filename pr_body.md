- Fixed tasks for idempotency and FQCN
- Added OS-family guards to distro-specific tasks
- Configured .yamllint with required standard rules
- Cleaned up README.md and AGENTS.md documentation
- Synchronized requirements.yml with molecule/default/requirements.yml
- Updated CI/CD to modern astral-sh/setup-uv

Test Plan:
- [x] Linting passed (yamllint + ansible-lint)
- [x] Molecule test passed locally (converge, idempotence, verify)
- [ ] CI pipeline passes on this branch

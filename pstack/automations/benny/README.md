# benny

benny gives you two agent automations for slack issue reports. one triages each report. the other reproduces confirmed bugs and may prepare a small draft fix.

the files in this directory are dormant setup and automation sources. they do not appear as slash skills.

## set it up

1. point your agent at [`FOR_AGENTS.md`](./FOR_AGENTS.md) and name the target repository.
2. let setup merge this whole directory into the target at `.agent/automations/benny/`. it must preserve destination-only files and review conflicts instead of overwriting local edits.
3. let setup make pstack resolvable in the target repository's project scope, so the shared dependencies (`how`, `why`, `tdd`, `unslop`, the principle skills) load for the automation's agent. the mechanism is host-specific: a committed project settings file that enables the plugin, a vendored copy of `skills/` in the repo, or a submodule. whichever you pick, it has to be committed, because the automation checks out the repo fresh on every run.

4. keep user-owned configuration outside the copied pack, for example in `.agent/benny/`. adapt [`configuration.example.yaml`](./templates/configuration.example.yaml) and [`feature-map.example.md`](./skills/reproduce-and-fix-issues/references/feature-map.example.md).
5. commit whatever makes pstack resolvable, `.agent/automations/benny/`, and any secret-free configuration before enabling either automation.
6. review each new automation draft or update existing automations in your host's automation editor. then send a harmless test report and verify every source-channel post stays in the original thread.

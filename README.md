# ☸️ K8s Dojo

An interactive Kubernetes training bridge — learn the cluster the way it actually thinks. A single, self-contained HTML page. No build step, no dependencies, no network.

**🔗 Live: https://shaqa3.github.io/k8s-dojo/**

## Run it

Just open the file:

```bash
open index.html          # macOS
# or serve it locally:
python3 -m http.server 8000   # then visit http://localhost:8000
```

## What's inside

- **Concepts** — 23 deep-dive cards organized into a belt progression (White → Black). Each opens a slide-over with the mental model, why it exists, the gotchas that actually bite people, a real manifest, and practice commands.
- **Cluster Lab** — the centerpiece. A live cluster diagram and a *simulated* `kubectl` terminal share one reactive state driven by a real reconcile loop:
  - `kubectl scale deployment web --replicas=5` — watch the scheduler place pods.
  - `kubectl delete pod <name>` — watch a controller heal it (a bare `kubectl run` pod stays gone).
  - `kubectl run oops --image=notreal` — see ImagePullBackOff.
  - `kubectl cordon` / `drain` — see scheduling and eviction.
  - Plus `describe`, `logs`, `expose`, `rollout`, command history (↑/↓), and quick-start chips.
- **Trials** — concept questions and fix-the-broken-manifest challenges. Answers reveal the reasoning and raise your belt rank.
- **RBAC** — an interactive `can-i` simulator. Build "Can [subject] [verb] [resource] in [namespace]?" and see ALLOW/DENY plus exactly which Role/ClusterRole binding decides it. Shows how RBAC is allow-only and additive, and how a RoleBinding scopes a ClusterRole to one namespace. Also runs as `kubectl auth can-i <verb> <resource> --as=<subject>` in the Cluster Lab terminal.

## Notes

- The simulated `kubectl` is a teaching model, not a real Kubernetes API. `apply -f` is not wired to a file editor — use `create` instead.
- Progress (studied concepts, trial score, rank) persists in your browser via `localStorage`.
- Light/dark theme toggle in the header; respects `prefers-reduced-motion`.

## Structure

```
k8s-dojo/
  index.html    # the entire app — markup, CSS, and JS in one file
  README.md
```

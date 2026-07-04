# duet

**Fable plans. Opus executes.**

A tiny Claude Code setup that splits the work between two Claude models. Fable is the architect: it thinks, breaks the task into precise work orders, and reviews. Opus is the executor: it makes the real edits and runs the commands. It runs on your Claude subscription. No API key, nothing metered.

*Version française plus bas.*

## English

### Install

Copy the two files into your global Claude config:

```bash
mkdir -p ~/.claude/agents ~/.claude/commands
cp agents/opus-executor.md   ~/.claude/agents/
cp commands/duet.md          ~/.claude/commands/
```

On Windows: `%USERPROFILE%\.claude\agents\` and `%USERPROFILE%\.claude\commands\`.

### Use

1. Set your model to Fable: run `/model` and pick Fable (if your plan offers it).
2. Run `/duet <your task>`.

Fable plans and hands each work order to the `opus-executor` subagent, which runs on Opus and does the real work. Fable reviews every report and keeps going until the task is done.

### What is in here

* `commands/duet.md` the `/duet` command. It tells the main model to act as the architect and delegate.
* `agents/opus-executor.md` the subagent that runs on Opus, does the reading and editing, and reports back a short outcome.

### Why it stays cheap

The planner is the expensive model, so the flow keeps its context tiny: the architect never reads files or runs commands itself. All reading, editing, and recon happen in the executor's own isolated context, and only short outcome reports flow back. Fewer, larger work orders, fanned out in parallel, replace long chains of tiny steps, and the architect checkpoints for a /compact between phases. You keep the planner's full reasoning power while a long session stays light.

### Note

The split is enforced by the prompt: the main agent still has file tools, and `/duet` tells it to delegate instead of coding directly.

## Français

### Installation

Copie les deux fichiers dans ta config Claude globale:

```bash
mkdir -p ~/.claude/agents ~/.claude/commands
cp agents/opus-executor.md   ~/.claude/agents/
cp commands/duet.md          ~/.claude/commands/
```

Sur Windows: `%USERPROFILE%\.claude\agents\` et `%USERPROFILE%\.claude\commands\`.

### Utilisation

1. Mets ton modèle à Fable: lance `/model` et choisis Fable (si ton forfait l'offre).
2. Lance `/duet <ta tâche>`.

Fable planifie et passe chaque ordre de travail au subagent `opus-executor`, qui roule sur Opus et fait le vrai travail. Fable révise chaque rapport et continue jusqu'à ce que ce soit fini.

### Ce qu'il y a ici

* `commands/duet.md` la commande `/duet`. Elle dit au modèle principal d'agir comme architecte et de déléguer.
* `agents/opus-executor.md` le subagent qui roule sur Opus, fait la lecture et les modifications, et renvoie un court rapport.

### Pourquoi ça reste léger

Le planificateur est le modèle coûteux, alors le flow garde son contexte minuscule: l'architecte ne lit jamais de fichiers et ne lance jamais de commandes lui-même. Toute la lecture, l'édition et la reconnaissance se font dans le contexte isolé de l'executor, et seuls de courts rapports de résultat reviennent. Moins de work orders mais plus gros, lancés en parallèle, remplacent les longues chaînes de micro-étapes, et l'architecte propose un /compact entre les phases. Tu gardes toute la puissance de raisonnement du planificateur pendant qu'une longue session reste légère.

### Note

Le split est imposé par le prompt: l'agent principal a encore les outils de fichier, et `/duet` lui dit de déléguer au lieu de coder directement.

## License

MIT.

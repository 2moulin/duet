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
* `agents/opus-executor.md` the subagent that runs on Opus and does the editing.

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
* `agents/opus-executor.md` le subagent qui roule sur Opus et fait les modifications.

### Note

Le split est imposé par le prompt: l'agent principal a encore les outils de fichier, et `/duet` lui dit de déléguer au lieu de coder directement.

## License

MIT.

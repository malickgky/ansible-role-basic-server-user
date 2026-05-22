# Ansible Project - Basic Server & User Setup

## Prérequis

- Ansible installé sur ta machine (`pip install ansible`)
- Clé SSH générée (`ssh-keygen -t rsa -b 4096`)
- Accès SSH root vers les VMs cibles

## Structure du projet

```
ansible-project/
├── inventory/
│   └── hosts.ini          # Liste des VMs cibles
├── roles/
│   ├── basic-server/      # Rôle configuration serveur
│   └── basic-user/        # Rôle gestion utilisateurs
├── playbooks/
│   └── site.yml           # Playbook principal
├── ansible.cfg            # Configuration Ansible
└── .vscode/
    ├── tasks.json          # Tâches VSCode (Ctrl+Shift+B)
    ├── settings.json       # Paramètres VSCode
    └── extensions.json     # Extensions recommandées
```

## Configuration avant de démarrer

### 1. Modifier l'inventaire
Éditer `inventory/hosts.ini` et renseigner les IPs de tes VMs.

### 2. Ajouter la clé SSH de elie.lamah
Dans `playbooks/site.yml`, compléter le champ `sshkeys` :
```yaml
sshkeys:
  - "ssh-rsa AAAAB3Nza... elie.lamah@machine"
```

### 3. Copier ta clé SSH sur les VMs
```bash
ssh-copy-id 
```

## Lancer le workflow dans VSCode

| Raccourci | Action |
|-----------|--------|
| `Ctrl+Shift+B` | Lancer le playbook complet |
| `Ctrl+Shift+P` → "Exécuter la tâche" | Choisir une tâche spécifique |

## Tâches disponibles

| Tâche | Description |
|-------|-------------|
| 🚀 Lancer Playbook complet | Exécute les 2 rôles |
| 👤 Lancer uniquement basic-user | Seulement le rôle user |
| 🖥️ Lancer uniquement basic-server | Seulement le rôle server |
| 🔍 Ping toutes les VMs | Vérifie la connectivité |
| 🧪 Dry-run (check mode) | Simule sans appliquer |
| 📋 Lister les hôtes | Affiche les VMs de l'inventaire |

# 🐚 Minishell

## 🎯 Objectif du projet

Le projet **Minishell** consiste à créer un interpréteur de commandes inspiré de `bash`. L'objectif est d'explorer et de maîtriser les concepts fondamentaux des systèmes d'exploitation Unix : la gestion des processus (`fork`, `execve`), la communication inter-processus (`pipe`), la manipulation des descripteurs de fichiers, et le traitement des signaux système.

---

## ✨ Fonctionnalités implémentées

* 🔄 **Exécution des commandes :** Gestion des chemins absolus, relatifs et recherche automatique via la variable d'environnement `PATH`.
* 📜 **Redirections & Pipes :** 
  * Redirections d'entrée/sortie (`<`, `>`, `>>`)
  * Heredoc (`<<`)
  * Enchaînement de commandes avec des pipes (`|`)
* 🔤 **Parsing avancé :** 
  * Gestion des guillemets simples (`'`) et doubles (`"`) avec des règles de citation spécifiques.
  * Expansion des variables d'environnement (ex: `$USER`, `$?`).
* ⚡ **Signaux :** Gestion interactive de `Ctrl+C`, `Ctrl+\` et `Ctrl+D` similaire à un vrai shell.
* 🛠️ **Builtins intégrés :** `echo` (avec `-n`), `cd`, `pwd`, `export`, `unset`, `env`, et `exit`.

---

## 🏗️ Architecture & Fonctionnement

Le programme se décompose généralement en plusieurs grandes étapes logiques :
1. **Lecture (Prompt) :** Affichage d'un prompt dynamique et récupération de la ligne de commande via `readline`.
2. **Lexing / Parsing :** Découpage de la chaîne de caractères en tokens, interprétation des guillemets, des expansions et construction d'un arbre syntaxique ou d'une liste chaînée de commandes.
3. **Expansion :** Remplacement des variables par leurs valeurs.
4. **Execution :** Création des processus fils, configuration des redirections et des pipes, puis appel des fonctions d'exécution (`execve` ou exécution des builtins).

---

## 🚀 Installation & Utilisation

Clone le dépôt, compile le projet à l'aide du `Makefile` fourni, puis lance le binaire :

```bash
git clone https://github.com/RobinM258/Minishell.git
cd Minishell
make
./minishell

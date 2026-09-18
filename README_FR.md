# Automatisation Intelligente de la Gestion des Courriels avec Microsoft Copilot Studio

Ce dépôt documente un flux de travail avancé pour la classification et la gestion autonome des courriels. Conçu pour optimiser les processus administratifs et améliorer la productivité opérationnelle, le système utilise des agents d'intelligence artificielle pour évaluer, acheminer et traiter les messages entrants en temps réel.

Cette implémentation reflète l'application pratique des outils d'IA pour renforcer la performance organisationnelle, en réduisant le temps consacré aux tâches répétitives et en priorisant l'attention sur les actions critiques.

## 📐 Architecture du Flux de Travail

Le système repose sur une architecture de nœuds interconnectés dans Microsoft Copilot Studio :

![Architecture du Flux de Travail](assets/image_34d707.png) *(Assurez-vous de télécharger l'image dans un dossier nommé 'assets')*

*   **Déclencheur Principal :** Connecteur Office 365 ("When a new email arrives") qui capture de manière autonome les métadonnées, l'importance et le contenu des messages entrants.
*   **Moteur de Classification (Classify) :** Utilise le modèle Claude Sonnet 4.6 pour évaluer dynamiquement l'expéditeur, l'objet, le corps du message et les pièces jointes, catégorisant le courriel selon des voies d'action spécifiques.

## ⚙️ Acheminement et Exécution des Agents

| Catégorie de Courriel | Séquence de Nœuds | Action Exécutée et Intégrations (MCP) |
| :--- | :--- | :--- |
| **Meeting** (Réunion) | `Meeting Logic` | L'agent extrait le contexte et utilise l'outil Calendrier pour générer et envoyer automatiquement une invitation Teams. |
| **Reply Requested** (Réponse) | `Copilot` ➔ `Email Drafter` | M365 Copilot analyse l'historique ; l'agent rédacteur utilise l'outil Courriel pour structurer et sauvegarder une réponse dans les brouillons. |
| **Priority** (Priorité) | `Agent` ➔ `Human review` ➔ `If/Else` | Un agent résume le contenu urgent et envoie une demande d'approbation via Teams. Selon la validation humaine, il planifie une réunion urgente ou envoie un courriel de suivi différé. |
| **Information** (Informatif) | `Info Sorter` | Identifie les courriels de lecture, gère le message dans la boîte de réception et envoie une notification résumée via Microsoft Teams. |
| **Other** (Autres) | N/A | Mécanisme de sécurité pour capturer la correspondance ne répondant pas aux paramètres principaux. |

## 🛠️ Technologies et Compétences Clés

*   **Microsoft Copilot Studio & Model Context Protocol (MCP) :** Orchestration des flux et assignation d'outils natifs (Mail, Calendar, Teams) à des agents autonomes.
*   **Ingénierie de Prompts et LLMs :** Conception d'instructions précises et injection de variables dynamiques pour le traitement de la logique conditionnelle.
*   **Optimisation des Processus (Human-in-the-loop) :** Intégration stratégique de points de validation humaine dans les processus critiques (courriels prioritaires), assurant le contrôle de la qualité.

---
**Développé par :** Camilo Salinas[cite: 1, 2]  
**Profil :** Spécialiste en intelligence d'affaires et analytique avec plus de 10 ans d'expérience professionnelle en administration, contrôle interne et optimisation des processus[cite: 1, 2].

[English](README.md) · **Français**

# Awesome Human MCPs

> Une liste organisée de serveurs MCP qui permettent aux agents IA de déléguer des tâches à de vrais humains.

Le chaînon manquant entre les agents IA et le monde physique. Quand votre agent ne peut pas passer un appel, récupérer un colis ou assister à une réunion : ces MCP comblent l'écart.

---

## Places de marché — l'IA embauche des humains

| Plateforme | MCP | Tâches | Tarifs | Notes |
|----------|-----|-------|---------|-------|
| [RentAHuman.ai](https://rentahuman.ai/) | `https://rentahuman.ai/mcp` | Courses physiques, photos, réunions, signature de documents | 15-175 $/h | 645 000+ travailleurs inscrits, 100+ pays. [Guide MCP](https://rentahuman.ai/blog/mcp-integration-guide) |
| [HumanMCP.ai](https://www.humanmcp.ai/) | `https://www.humanmcp.ai/mcp` | Appels téléphoniques, recherche, vérification, contenu localisé | ~28 $/tâche | Spécialisé dans les tâches que l'IA ne peut fondamentalement pas faire (appels vocaux, vérification physique) |
| [HireAHuman.ai](https://www.hireahuman.ai/) | `https://www.hireahuman.ai/mcp` | Travail freelance, modèle de partage de revenus | Variable | Les revenus de l'automatisation financent les moyens de subsistance humains |

## Couches d'approbation — humain dans la boucle

| Plateforme | MCP | Cas d'usage | Installation |
|----------|-----|----------|---------|
| [GoToHuman](https://gotohuman.com) | `npx @gotohuman/mcp-server` | Flux d'approbation avant des actions sensibles | [GitHub](https://github.com/gotohuman/gotohuman-mcp-server) |
| [ask-human-mcp](https://github.com/Masony817/ask-human-mcp) | Auto-hébergé | Zéro config : l'IA écrit dans un markdown, l'humain édite, l'agent reprend | GitHub |
| [human-in-the-loop](https://github.com/KOBA789/human-in-the-loop) | Auto-hébergé (Rust) | L'IA pose des questions via Discord, attend une réponse | 221 étoiles |
| [human-mcp](https://github.com/upamune/human-mcp) | Auto-hébergé (Python) | L'humain comme serveur MCP (outils œil, main, bouche). UI Streamlit | 45 étoiles |
| [mcp-human-loop](https://github.com/boorich/mcp-human-loop) | Auto-hébergé | Score les requêtes sur la complexité/le risque pour décider si une revue humaine est nécessaire | GitHub |
| [telegram-human-in-the-loop](https://github.com/theohero/telegram-human-in-the-loop) | Auto-hébergé | HITL via Telegram | GitHub |

## Gig economy — livraison et services

| Plateforme | MCP | Type | Notes |
|----------|-----|------|-------|
| [DoorDash Drive](https://developer.doordash.com) | [MCP communautaire](https://github.com/JordanDalton/DoorDash-MCP-Server) | Logistique B2B (pas de commande consommateur) | 14 outils, nécessite des identifiants développeur |
| [Instacart](https://docs.instacart.com/developer_platform_api/guide/tutorials/mcp/) | `https://mcp.instacart.com/mcp` | Officiel. Recettes + listes de courses | Clé API requise |
| Uber Eats | [MCP communautaire](https://github.com/ericzakariasson/uber-eats) | POC basé sur Playwright | Expérimental |
| Fiverr | [Bright Data MCP](https://brightdata.com/ai/mcp-server/fiverr) | Scraper (5000 requêtes gratuites/mois) | Pas d'API officielle |

## Pas encore disponible

| Plateforme | Statut |
|----------|--------|
| TaskRabbit | Pas d'API, pas de MCP |
| Upwork | Pas de MCP. Le PDG a confirmé que des agents IA tentent déjà de poster des offres (mars 2026) |
| Uber Rides | Une passerelle MCP interne existe mais n'est pas publique |

---

## Démarrage rapide

À ajouter à votre config MCP Claude Code (`~/.claude.json`) :

```json
{
  "mcpServers": {
    "rentahuman": {
      "type": "http",
      "url": "https://rentahuman.ai/mcp"
    },
    "gotohuman": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@gotohuman/mcp-server"],
      "env": {
        "GOTOHUMAN_API_KEY": "your-key"
      }
    },
    "instacart": {
      "type": "http",
      "url": "https://mcp.instacart.com/mcp"
    },
    "humanmcp": {
      "type": "http",
      "url": "https://www.humanmcp.ai/mcp"
    }
  }
}
```

Redémarrer Claude Code. Taper `/mcp` pour vérifier que les serveurs sont connectés.

---

## Au niveau du protocole : MCP Elicitation

La spécification MCP a ajouté **Elicitation** (juin 2025, brouillon) : un mécanisme intégré permettant à un serveur MCP de suspendre l'exécution et de demander une saisie structurée à l'utilisateur. C'est la réponse standardisée au humain-dans-la-boucle au niveau du protocole.

---

## Contexte industrie

- **RentAHuman.ai** a été lancé le 2 février 2026. Couvert par Nature, Newsweek, Futurism, Wired.
- Le **PDG d'Upwork** a révélé en mars 2026 que des agents IA tentent déjà de créer des comptes et d'embaucher des freelances.
- **DoorDash** a lancé l'app « Tasks » (19 mars 2026), qui paie des Dashers pour collecter des données d'entraînement IA.
- **Uber** a construit une passerelle MCP interne exposant tous ses endpoints. 84 % des développeurs Uber utilisent le codage agentique.

---

## Contribuer

Les PR sont bienvenues. Ajoutez de nouvelles plateformes, corrigez les liens morts, partagez votre expérience d'intégration.

## Licence

CC BY-NC-ND 4.0, voir [LICENSE.md](LICENSE.md).

Par [Ismaël Joffroy Chandoutis](https://ismaeljoffroychandoutis.com).

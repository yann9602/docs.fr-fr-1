---
title: Choisissez entre les applications web classiques et les applications de page unique
description: Architecture des applications web avec ASP.NET Core et Microsoft Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 5bae77fc4e0df9d0bc7fecfad25adfcee2419084
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Choisissez entre les applications Web classiques et les applications de Page unique (ZPS)

> « Par la loi de Atwood : toutes les applications qui peuvent être écrites en JavaScript, sera finalement être écrites en JavaScript. »  
> _\-Jeff Atwood_

## <a name="summary"></a>Résumé

Il existe deux approches générales pour la création d’applications web aujourd'hui : les applications web traditionnelles qui effectuent la plupart de la logique d’application sur le serveur et les applications à page unique (ZPS) qui effectuent la plupart de la logique d’interface utilisateur dans un navigateur web, communication avec le serveur web principalement à l’aide des API web. Une approche hybride est également possible, plus simples étant héberger un ou plusieurs type secondaire applications riches au sein d’une application web classique plus importante.

Vous devez utiliser des applications web traditionnelles lorsque :

-   Exigences de votre application côté client sont simples ou même en lecture seule.

-   Votre application doit fonctionner dans les navigateurs sans prise en charge JavaScript.

-   Votre équipe est êtes pas familiarisé avec les techniques de développement JavaScript ou TypeScript.

Vous devez utiliser un SPA lorsque :

-   Votre application doit exposer une interface utilisateur élaborée avec de nombreuses fonctionnalités.

-   Votre équipe est familiarisé avec le développement de JavaScript ou TypeScript.

-   Votre application doit exposer déjà d’une API pour d’autres clients (internes ou publics).

En outre, les infrastructures SPA exigent une architecture et des connaissances en matière de sécurité. Ils rencontrent une évolution supérieure en raison de mises à jour fréquentes et des nouvelles infrastructures que les applications web traditionnelles. Configuration des processus de génération et de déploiement automatisés et l’utilisation des options de déploiement comme des conteneurs sont plus difficiles avec les applications SPA que les applications web classiques.

Amélioration de l’expérience utilisateur rendu possible par le modèle SPA doit être comparée de ces considérations.

## <a name="when-to-choose-traditional-web-apps"></a>Pour choisir les applications web classiques

Voici une explication plus détaillée des raisons précédemment indiqué pour le prélèvement des applications web traditionnelles.

**Votre application présente des exigences simples, éventuellement en lecture seule, côté client**

De nombreuses applications web sont principalement utilisées dans une disposition en lecture seule par la grande majorité de leurs utilisateurs. Les applications en lecture seule (ou en lecture principale) ont tendance à être beaucoup plus simples que celles maintenir et manipuler une grande partie de l’état. Par exemple, un moteur de recherche peut être constituée d’un point d’entrée unique avec une zone de texte et une deuxième page d’affichage des résultats de recherche. Les utilisateurs anonymes peuvent facilement envoyer des demandes, et il est peu d’intérêt pour une logique côté client. De même, application orientée public de blog ou contenu gestion d’un système généralement est principalement constitué du contenu avec peu le comportement côté client. Ces applications sont facilement créées en tant qu’applications web classique de serveur qui exécuter la logique sur le serveur web et d’effectuer le rendu HTML à afficher dans le navigateur. Le fait que chaque page unique du site possède sa propre URL qui peut être des signets et indexé par les moteurs de recherche (par défaut, sans avoir à ajouter comme une fonction séparée de l’application) est également un avantage évident dans de tels scénarios.

**Votre application a besoin pour fonctionner dans les navigateurs sans prise en charge de JavaScript**

Les applications Web qui ont besoin pour fonctionner dans les navigateurs avec peu ou aucune prise en charge JavaScript doivent être écrit à l’aide de workflows d’application web classique (ou au moins être en mesure de revenir au comportement de ce type). SPAs nécessitent JavaScript côté client pour pouvoir fonctionner ; s’il n’est pas disponible, SPAs ne sont pas un bon choix.

**Votre équipe est êtes pas familiarisé avec les techniques de développement JavaScript ou TypeScript**

Si votre équipe ne connaît pas avec JavaScript ou TypeScript, mais s’est familiarisé avec le développement d’applications web côté serveur, ils seront probablement en mesure de fournir une application web classique plus rapidement que SPA. Sauf si l’apprentissage de programme SPAs est un objectif, ou l’expérience utilisateur offerte par SPA est requis, les applications web classiques sont un choix plus productif pour les équipes qui sont déjà familiarisés avec leur création.

## <a name="when-to-choose-spas"></a>Pour choisir SPAs

Voici une explication plus détaillée de pour choisir un style d’Applications à Page unique du développement de votre application web.

**Votre application doit exposer une interface utilisateur élaborée avec de nombreuses fonctionnalités**

SPAs peuvent prendre en charge les fonctionnalités côté client riche qui ne nécessitent pas recharger la page, comme les utilisateurs prennent des mesures ou naviguer entre les zones de l’application. SPAs peuvent charger plus rapidement, l’extraction de données en arrière-plan, et les actions utilisateur individuelles sont plus réactives, car les rechargements pleine page sont rares. SPAs peuvent prendre en charge les mises à jour incrémentielles, l’enregistrement des formulaires partiellement remplis ou les documents sans l’utilisateur clique sur un bouton pour envoyer un formulaire. SPAs peuvent prendre en charge des comportements côté client riches, tels que les glisser-déposer, beaucoup plus rapidement que les applications traditionnelles. SPAs peuvent être conçues pour s’exécuter dans un mode déconnecté, mettre à jour un modèle côté client qui sont synchronisés par la suite sur le serveur une fois qu’une connexion est rétablie. Vous devez choisir une application de style SPA si les exigences de votre application incluent des fonctionnalités enrichies qui va au-delà de ce qui offrent des formulaires HTML classiques.

Notez que fréquemment SPAs doivent implémenter les fonctionnalités qui sont intégrées à des applications web classiques, comme l’affichage d’une URL significative dans l’adresse barre reflétant l’opération en cours (et ce qui permet aux utilisateurs de signet ou un lien ciblé pour cette URL pour y revenir). SPAs doivent permettent également aux utilisateurs du navigateur boutons Précédent et suivant de résultats qui ne sont pas surprendre les.

**Votre équipe est familiarisé avec le développement de JavaScript ou TypeScript**

L’écriture SPAs nécessaire de connaître JavaScript ou TypeScript et les bibliothèques et les techniques de programmation côté client. Votre équipe doit être compétent en écrire moderne JavaScript à l’aide d’une infrastructure SPA comme angulaire.

> ### <a name="references--spa-frameworks"></a>Références – SPA infrastructures
> - **AngularJS**  
> <https://angularjs.org/>
> - **Comparaison entre les infrastructures JavaScript courantes 4**  
> <https://www.developereconomics.com/Feature-Comparison-of-4-Popular-js-MV-Frameworks>

**Votre application doit exposer déjà une API pour d’autres clients (internes ou publics)**

Si vous êtes déjà en charge une API web pour une utilisation par d’autres clients, elle peut nécessiter moins d’efforts pour créer une implémentation de SPA qui tire parti de ces API, plutôt que de reproduire la logique de formulaire côté serveur. SPAs utilisent beaucoup d’API web pour les données de requête et de mise à jour lorsque les utilisateurs interagissent avec l’application.

## <a name="decision-table--traditional-web-or-spa"></a>Table de décision – Web classique ou SPA

Le tableau ci-dessous résume certains facteurs à prendre en compte lors du choix entre une application web classique et SPA base.

  | **Facteur** | **Application Web traditionnel** | **Application à Page unique** |
  |---|---|---|
  | Connaissance de l’équipe requises avec JavaScript/TypeScript | **Minimale** | **Obligatoire** |
  | Prise en charge des navigateurs sans script | **Prise en charge** | **Non pris en charge** |
  | Comportement de l’Application côté Client minimale | **Convient parfaitement** | **Excessifs** |
  | Exigences de l’Interface utilisateur riches et complexes | **Limitée** | **Convient parfaitement** |

>[!div class="step-by-step"]
[Précédente] (modern-web-applications-characteristics.md) [suivant](architectural-principles.md)

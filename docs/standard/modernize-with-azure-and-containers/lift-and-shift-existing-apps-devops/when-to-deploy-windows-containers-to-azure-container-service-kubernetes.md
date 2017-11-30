---
title: "Moment de déployer des conteneurs Windows dans le Service de conteneur Azure (autrement dit, Kubernetes)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Moment de déployer des conteneurs Windows dans le Service de conteneur Azure (autrement dit, Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Moment de déployer des conteneurs Windows dans le Service de conteneur Azure (autrement dit, Kubernetes)

Service de conteneur Azure permet d’optimiser la configuration des outils open source populaires et technologies utilisées spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité de vos conteneurs et lors de la configuration de votre application. Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrator. Service de conteneur Azure gère l’infrastructure pour vous.

Si vous utilisez déjà orchestrators open source comme Kubernetes, Docker Swarm ou contrôleur de domaine/système d’exploitation, vous n’avez pas besoin de modifier vos méthodes de gestion existant pour déplacer les charges de travail conteneur dans le cloud. Utilisez les outils de gestion d’application que vous êtes déjà familiarisé avec et se connectez via les points de terminaison API standards pour l’orchestrateur de votre choix.

Tous ces orchestrators sont déjà rodées environnements Si vous utilisez des conteneurs Linux Docker, mais ils également prise en charge des conteneurs Windows comme de 2017 (certaines précédemment, d’autres plus récente, en fonction de l’orchestrateur).

Par exemple, dans Kubernetes, prise en charge les conteneurs est natif (acteur), à l’aide de conteneurs Windows sur Kubernetes est également très efficace et fiable (dans l’aperçu jusqu’au début se situent 2017).

>[!div class="step-by-step"]
[Précédent](when-to-deploy-windows-containers-to-service-fabric.md)
[Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)

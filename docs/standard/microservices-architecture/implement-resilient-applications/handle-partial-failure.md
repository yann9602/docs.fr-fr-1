---
title: "Gestion des défaillances partielles"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Gestion des défaillances partielles"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7d16acf3de2d395da70e8f46e59c129dec24f71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="handling-partial-failure"></a>Gestion des défaillances partielles

Dans les systèmes distribués tels que les applications basées sur des microservices, il existe un risque de permanente de défaillance partielle. Par exemple, un seul microservice/conteneur peut échouer ou n’est peut-être pas disponible pour répondre pendant une courte période, ou un ordinateur virtuel ou un serveur unique peut se bloquer. Étant donné que les clients et services sont des processus distincts, un service n’est peut-être pas en mesure de répondre à une demande du client à un moment opportun. Le service peut être surchargés et répond très lentement à des demandes ou ne simplement pas être accessible pendant une courte période en raison de problèmes de réseau.

Par exemple, considérez la page de détails de commande à partir de l’eShopOnContainers exemple d’application. Si le tri microservice ne répond pas quand l’utilisateur tente d’envoyer une commande, une mauvaise implémentation du processus client (l’application web MVC) — par exemple, si le code client à utiliser un RPC synchrones sans délai d’attente, susceptibles de bloquer indéfiniment threads attente d’une réponse. Outre la création d’une expérience utilisateur incorrect, chaque attente ne répond pas consomme ou bloque un thread, et les threads sont particulièrement utiles dans les applications hautement évolutives. S’il existe de nombreux threads bloqués, finalement runtime de l’application peut manquer de threads. Dans ce cas, l’application peut devenir globalement ne répond pas au lieu de simplement partiellement qui ne répond pas, comme indiqué dans la Figure 10-1.

![](./media/image1.png)

**Figure 10-1**. Défaillances partielles en raison des dépendances qui affectent la disponibilité de thread de service

Dans une grande application microservices, tout échec partiel peut être élargie, surtout si la plupart de l’interaction de microservices interne est basée sur les appels HTTP synchrones (ce qui est considéré comme un anti-modèle). Pensez à un système qui reçoit des millions d’appels par jour. Si votre système a une mauvaise conception est basée sur longues chaînes d’appels HTTP synchrones, ces appels entrants peuvent entraîner des millions de plus de (supposons un ratio de 1:4) les appels sortants à des dizaines de microservices interne en tant que dépendances synchrones. Cette situation est montre la Figure 10-2, en particulier de dépendance \#3.

![](./media/image2.png)

**Figure 10-2**. L’impact d’une conception incorrecte avec longues chaînes de requêtes HTTP

Échec intermittent est pratiquement garantie dans distribué et sur le cloud système, même si chaque dépendance lui-même a une excellente disponibilité. Ce doit être un fait que vous devez tenir compte.

Si vous ne pas concevoir et implémenter des techniques permettant de garantir la tolérance de pannes, même les petites à un temps mort peut amplifié. Par exemple, 50 dépendances avec 99,99 % de disponibilité se traduirait par plusieurs heures d’arrêt chaque mois en raison de cet effet. Lorsqu’une dépendance de microservice échoue lors du traitement d’un volume élevé de demandes, cet échec peut rapidement saturer tous les threads de requête disponibles dans chaque service et bloque toute l’application.

![](./media/image3.png)

**Figure 10-3**. Échec partiel amplifié par microservices avec longues chaînes d’appels HTTP synchrones

Pour minimiser ce problème, dans la section «*microservice asynchrone intégration appliquer l’autonomie de microservice*» (dans le chapitre architecture), nous vous permet d’utiliser la communication asynchrone entre interne invités microservices. Nous expliquent brièvement plus dans la section suivante.

En outre, il est essentiel que vous concevez votre microservices et les applications clientes pour gérer les défaillances partielles, autrement dit, pour créer des applications résilientes microservices et le client.


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (strategies.md de la défaillance partielle)

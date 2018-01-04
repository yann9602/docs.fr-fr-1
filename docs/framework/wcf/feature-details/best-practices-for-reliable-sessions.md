---
title: Meilleures pratiques pour les sessions fiables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c022db62103826aa89e9035fd36c050d1f7c0f84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-reliable-sessions"></a>Meilleures pratiques pour les sessions fiables

Cette rubrique décrit les meilleures pratiques des sessions fiables.

## <a name="setting-maxtransferwindowsize"></a>Définition de MaxTransferWindowSize

Les sessions fiables dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisent une fenêtre de transfert pour contenir des messages sur le client et sur le service. La propriété configurable <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indique combien de messages la fenêtre de transfert peut contenir.

Sur l’expéditeur, cela indique combien de messages la fenêtre de transfert peut contenir en attendant des accusés de réception ; pour le récepteur, il indique le nombre de messages en mémoire tampon pour le service.

Choisir la bonne taille a un impact sur l’efficacité du réseau et la capacité optimale du service. Les sections suivantes détaillent les éléments à prendre en compte lors du choix d’une valeur pour cette propriété et l’impact de la valeur.

La taille de fenêtre de transfert par défaut est de huit des messages.

### <a name="efficient-use-of-the-network"></a>Utilisation efficace du réseau

Dans ce contexte, le terme *réseau* correspond à tous les éléments utilisés comme base de communication entre un client (expéditeur) et un service (récepteur). Cela inclut les connexions de transport et de tout intermédiaire ou de ponts intermédiaires, y compris les routeurs SOAP ou proxys/pare-feu HTTP.

L'utilisation efficace du réseau garantit que sa capacité est pleinement utilisée. La quantité de données qui peuvent être transférées par seconde sur le réseau (*débit*) et le temps nécessaire pour transférer des données à partir de l’expéditeur au récepteur (*latence*) avoir un impact sur l’efficacité avec laquelle le réseau est utilisé.

Sur l'expéditeur, la propriété <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indique combien de messages sa fenêtre de transfert peut contenir en attendant des accusés de réception. Si la latence du réseau est élevée et afin de garantir un expéditeur réactif et une utilisation efficace du réseau, vous devez augmenter la taille de fenêtre de transfert.

Par exemple même si l’expéditeur suit la cadence de données, la latence peut être élevée si plusieurs intermédiaires existent entre l’expéditeur et le récepteur ou les données doivent traverser un intermédiaire avec perte de données ou un réseau. Par conséquent, l’expéditeur doit attendre les accusés de réception pour les messages dans sa fenêtre de transfert avant d’accepter de nouveaux messages à envoyer sur le câble. Plus la mémoire tampon avec une latence élevée, moins l’effet l’utilisation du réseau. Quant à eux, trop élevée une taille de fenêtre de transfert peut avoir un impact sur le service, car le service peut avoir besoin de rattraper la vitesse élevée de données envoyées par le client.

### <a name="running-the-service-to-capacity"></a>Le service en cours d’exécution à la capacité

Comme le réseau est utilisé efficacement, dans l’idéal, vous souhaitez également le service s’exécute à capacité optimale. La propriété de la taille de la fenêtre de transfert sur le récepteur indique combien de messages le récepteur peut mettre en mémoire tampon. Cette mise en mémoire tampon permet non seulement de contrôler le flux du réseau mais également d'exécuter le service à capacité complète. Par exemple, si la mémoire tampon est un message et les messages arrivent plus rapidement que le service peut les traiter, puis le réseau peut supprimer des messages et la capacité peut être gaspillée ou sous-utilisée.

À l’aide d’une mémoire tampon d’augmente la disponibilité du service reçoit et met en mémoire tampon un message lors du traitement des messages précédemment reçus simultanément.

Nous vous recommandons d’utiliser le même `MaxTransferWindowSize` sur l’expéditeur et le récepteur.

### <a name="enabling-flow-control"></a>Activation du contrôle de flux

*Contrôle de flux* est un mécanisme qui garantit que l’expéditeur et récepteur au même rythme entre eux, autrement dit, les messages sont consommés et traités aussi rapidement qu’ils sont générés. La taille de la fenêtre de transfert sur le client et sur le service garantit que l’expéditeur et le récepteur respectent une fenêtre de synchronisation raisonnable.

Il est vivement recommandé de définir la propriété <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> à `true` lorsque vous utilisez une session fiable entre un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client et un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.

## <a name="setting-maxpendingchannels"></a>Définition de MaxPendingChannels

Lorsque vous écrivez un service qui permet la communication de session fiable à partir de clients, il est possible que plusieurs clients d’établir une session fiable pour le service en même temps. La réponse du service dans ces situations dépend de la propriété `MaxPendingChannels`.

Lorsque l'expéditeur crée un canal de session fiable vers un récepteur, une négociation entre eux établit une session fiable. Après avoir établi la session fiable, le canal est mis en file d'attente pour l'acceptation par le service. La propriété `MaxPendingChannels` indique combien de canaux peuvent être dans cet état.

Il est possible que le service doit être dans un état où il ne peut pas accepter plus de canaux. Si la file d’attente est pleine, tenter d’établir une session fiable est rejetée et le client doit réessayer.

Il est également possible que les canaux en attente dans la file d’attente restent dans la file d’attente pour une durée plus longue. En attendant, délai d’inactivité de la session fiable peut se produire, provoquant le canal à passer à un état d’erreur.

Lorsque vous écrivez un service servant plusieurs clients simultanément, vous devez définir une valeur qui est adaptée à vos besoins. Définition d’une valeur trop élevée pour le `MaxPendingChannels` propriété a un impact sur votre jeu de travail.

La valeur par défaut <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> est de quatre couches.

## <a name="reliable-sessions-and-hosting"></a>Les sessions fiables et hébergement

Lorsque web qui héberge un service qui utilise des sessions fiables, vous devez conserver les points importants suivants à l’esprit :

- Les sessions fiables sont avec état, et l’état est géré dans AppDomain. Cela signifie que tous les messages qui font partie d'une session fiable doivent être traités dans le même AppDomain. Batteries de serveurs Web et les domaines privés web où la taille de la batterie de serveurs ou d’un domaine privé est supérieure à un seul nœud ne peut pas garantir cette contrainte.

- Les sessions fiables à l’aide des canaux HTTP doubles (par exemple, à l’aide de `WsDualHttpBinding`) peuvent nécessiter plus que la valeur par défaut de deux connexions par-client HTTP. Cela signifie qu'une session fiable duplex peut nécessiter jusqu'à deux connexions chacune d’elles étant donné que les messages d’application et de protocole simultanés peuvent être transférés dans chacune d’elles à un moment donné. Sous certaines conditions selon le modèle d’échange de messages du service, cela signifie qu’il est possible d’interbloquer un service hébergé sur le web utilisant HTTP double et les sessions fiables. Pour augmenter le nombre de connexions HTTP autorisées par client, ajoutez le code suivant au fichier de configuration approprié (par exemple, *web.config* du service en question) :

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  La valeur de la `maxconnection` attribut est le nombre de connexions nécessaires. Le minimum recommandé dans ce cas est de quatre connexions.

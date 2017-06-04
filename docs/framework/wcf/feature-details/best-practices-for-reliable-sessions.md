---
title: "Meilleures pratiques pour les sessions fiables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Meilleures pratiques pour les sessions fiables
Cette section aborde les meilleures pratiques des sessions fiables.  
  
## Définition de MaxTransferWindowSize  
 Les sessions fiables dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisent une fenêtre de transfert pour contenir des messages sur le client et sur le service.  La propriété configurable <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indique combien de messages la fenêtre de transfert peut contenir.  
  
 Sur l'expéditeur, cela indique combien de messages la fenêtre de transfert peut contenir en attendant les accusés de réception ; sur le récepteur, cela indique combien de messages sont mis en mémoire tampon pour le service.  
  
 Le choix de la taille a un impact sur l'efficacité d'utilisation du réseau et sur la capacité optimale à laquelle le service s'exécute.  Les sections suivantes détaillent les éléments à prendre en compte lors du choix d'une valeur pour cette propriété et l'impact de cette valeur.  
  
 La taille par défaut de la fenêtre de transfert est de 8 messages.  
  
### Utilisation efficace du réseau  
 Le terme *réseau* fait ici référence à toute connexion entre un client \(expéditeur\) et un service \(récepteur\) utilisée comme base de communication.  Cela inclut les connexions de transport et les intermédiaires ou ponts intermédiaires, y compris les routeurs SOAP ou proxys\/pare\-feu HTTP.  
  
 L'utilisation efficace du réseau garantit que sa capacité est pleinement utilisée.  La quantité de données pouvant être transférée par seconde sur le réseau \(*vitesse de transmission de données*\) et le temps requis pour transférer des données de l'expéditeur au récepteur \(*latence*\) ont un impact sur l'utilisation efficace du réseau.  
  
 Sur l'expéditeur, la propriété <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indique combien de messages sa fenêtre de transfert peut contenir en attendant des accusés de réception.  Donc, si le temps de réponse du réseau est élevé, pour garantir un expéditeur réactif et une utilisation efficace du réseau, vous devez augmenter la taille de la fenêtre de transfert.  
  
 Par exemple, même si l'expéditeur suit la vitesse de transmission de données, la latence peut être élevée si plusieurs intermédiaires existent entre l'expéditeur et le récepteur ou en cas de pertes au niveau d'un intermédiaire ou du réseau.  Donc l'expéditeur doit attendre les accusés de réception des messages dans sa fenêtre de transfert avant d'accepter d'envoyer de nouveaux messages sur le fil.  Plus la mémoire tampon est petite et la latence est élevée, moins l'utilisation du réseau sera efficace.  En revanche, une taille de fenêtre de transfert trop importante peut avoir un impact sur le service parce que ce dernier devra peut\-être atteindre la vitesse de transmission élevée du client.  
  
### Exécution du service en fonction de la capacité  
 Une fois que le réseau est utilisé efficacement, il convient également de s'assurer que le service s'exécute à capacité optimale.  La propriété de la taille de la fenêtre de transfert sur le récepteur indique combien de messages le récepteur peut mettre en mémoire tampon.  Cette mise en mémoire tampon permet non seulement de contrôler le flux du réseau mais également d'exécuter le service à capacité complète.  Par exemple, si la mémoire tampon est 1 et les messages arrivent plus vite que le service ne peut les traiter, alors le réseau peut supprimer des messages et la capacité du réseau peut être gaspillée ou sous\-utilisée.  
  
 L'utilisation d'une mémoire tampon augmente la disponibilité du service car ce dernier reçoit et met en mémoire tampon simultanément le message, en traitant les messages reçus précédemment.  
  
 Il est recommandé d'utiliser le même `MaxTransferWindowSize` sur à la fois l'expéditeur et récepteur.  
  
### Activation du contrôle de flux  
 Le contrôle de flux est un mécanisme qui garantit que l'expéditeur et le récepteur fonctionnent au même rythme, autrement dit, que les messages sont consommés et traités aussi rapidement qu'ils sont produits.  La taille de la fenêtre de transfert sur le client et sur le service garantit que l'expéditeur et le récepteur respectent une fenêtre de synchronisation raisonnable.  
  
 Il est hautement recommandé d'attribuer à la propriété <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> la valeur "vraie" lorsque vous utilisez une session fiable entre un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Définition de MaxPendingChannels  
 Lors de l'écriture d'un service qui active la communication de session fiable de clients différents, il est possible que plusieurs clients établissent une session fiable vers le service en même temps.  La réponse du service dans ces situations dépend de la propriété `MaxPendingChannels`.  
  
 Lorsque l'expéditeur crée un canal de session fiable vers un récepteur, une négociation entre eux établit une session fiable.  Après avoir établi la session fiable, le canal est mis en file d'attente pour l'acceptation par le service.  La propriété `MaxPendingChannels` indique combien de canaux peuvent être dans cet état.  
  
 Il est possible que le service soit dans un état où il ne peut plus accepter de canaux.  Si la file d'attente est complète, une tentative d'établir une session fiable est repoussée et le client doit réessayer.  
  
 Il se peut également que les canaux en file d'attente y restent pour une plus longue durée.  Entre\-temps, le délai d'inactivité sur la session fiable peut entrer en action, provoquant la transition du canal à l'état de faute.  
  
 Par conséquent, lors de l'écriture d'un service servant plusieurs clients simultanément, vous devez définir une valeur appropriée à vos besoins.  Une valeur trop haute pour la propriété `MaxPendingChannels` aura un impact sur votre plage de travail.  
  
 La valeur par défaut <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> est 4.  
  
## Sessions fiables et hébergement  
 En cas d'hébergement Web d'un service utilisant des sessions fiables, vous devez tenir compte des considérations importantes suivantes :  
  
-   Les sessions fiables sont avec état, et l'état est géré dans AppDomain.  Cela signifie que tous les messages qui font partie d'une session fiable doivent être traités dans le même AppDomain.  Les batteries de serveurs web et les domaines privés web dont la taille est supérieure à 1 ne peuvent pas garantir l'application de cette contrainte.  
  
-   Les sessions fiables utilisant des canaux HTTP doubles \(par exemple, `WsDualHttpBinding`\) peuvent nécessiter plus que les connexions HTTP par défaut de 2 pour chaque client.  Cela signifie qu'une session fiable duplex peut requérir jusqu'à 2 connexions dans chaque direction, parce que les messages d'application et de protocole simultanés peuvent être transférés dans chaque direction à tout moment.  Autrement dit, sous certaines conditions, selon le modèle d'échange de messages du service, il est possible d'interbloquer un service hébergé par Web utilisant HTTP double et des sessions fiables.  Pour augmenter le nombre de connexions HTTP autorisées par client, ajoutez ce qui suit au fichier de configuration pertinent \(par exemple, web.config du service en question\) :  
  
```  
<configuration>  
   <system.net>  
      <connectionManagement>  
         <add name = "*" maxconnection = "XX" />  
      </connectionManagement>  
   </system.net>  
</configuration>  
```  
  
 Où "XX" est le nombre de connexions exigées.  Le minimum dans ce cas doit être 4.
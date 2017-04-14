---
title: "Am&#233;liorations des performances de socket dans la version&#160;3.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Am&#233;liorations des performances de socket dans la version&#160;3.5
La classe d' <xref:System.Net.Sockets.Socket?displayProperty=fullName> a été améliorée dans la version 3,5 pour une utilisation par des applications qui utilisent l'E\/S asynchrone de réseau pour accomplir performances élevées.  Une série de nouvelles classes a été ajoutée dans le cadre d'un ensemble d'améliorations à la classe d' <xref:System.Net.Sockets.Socket> qui fournissent un autre modèle asynchrone qui peut être utilisé par des applications haute performance spécialisées de socket.  Ces améliorations ont été conçues spécifiquement pour les applications serveur réseau qui nécessitent une haute performance.  Une application peut utiliser le modèle asynchrone amélioré exclusivement, ou uniquement dans des zones réactives ciblées de leur application \(en recevant grandes quantités de données, par exemple\).  
  
## Améliorations de classe  
 La principale caractéristique de ces améliorations est qu'elles évitent l'allocation et la synchronisation répétées d'objets pendant les opérations d'E\/S de socket asynchrone à volume élevé.  Le modèle de design de début\/fin actuelle implémenté par la classe d' <xref:System.Net.Sockets.Socket> pour l'E\/S asynchrone de socket requiert un objet d' <xref:System.IAsyncResult?displayProperty=fullName> est alloué pour chaque opération de socket asynchrone.  
  
 Dans les nouvelles améliorations de classe d' <xref:System.Net.Sockets.Socket> , les opérations de socket asynchrones sont décrites par les objets de classes réutilisables d' <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=fullName> alloués et mis à jour par l'application.  Les applications de socket hautes performances connaissent mieux la quantité d'opérations de socket chevauchées qui doivent être soutenues.  L'application peut créer autant d'objets <xref:System.Net.Sockets.SocketAsyncEventArgs> que nécessaire.  Par exemple, si une application serveur doit faire accepter le socket 15 des opérations en attente à tout moment pour prendre en charge les taux entrantes de connexion client, elle peut allouer 15 objets réutilisables d' <xref:System.Net.Sockets.SocketAsyncEventArgs> à l'avance à cette fin.  
  
 Le modèle d'exécution d'une opération de socket asynchrone avec cette classe se compose des étapes suivantes :  
  
1.  Allocation d'un nouvel objet de contexte <xref:System.Net.Sockets.SocketAsyncEventArgs> ou obtention d'un objet gratuitement à partir d'un pool d'applications.  
  
2.  Définissez les propriétés sur l'objet de contexte d'exécution environ à exécuter \(la méthode délégué et la mémoire tampon de données de rappel, par exemple\).  
  
3.  Appel de la méthode de socket \(xxxAsync\) appropriée pour initialiser l'opération asynchrone.  
  
4.  Si la méthode asynchrone de socket \(xxxAsync\) retourne la valeur true dans le rappel, interrogez les propriétés de contexte pour l'état d'achèvement.  
  
5.  Si la méthode asynchrone de socket \(xxxAsync\) retourne la valeur false dans le rappel, l'opération effectuée de façon synchrone.  Les propriétés de contexte peuvent être interrogées pour le résultat d'opération.  
  
6.  Réutilisation du contexte pour une autre opération, remise de celui\-ci dans le pool ou élimination.  
  
 La durée de vie du nouvel objet de contexte asynchrone d'opération de socket est déterminée par les références dans les références de code et d'E\/S asynchrone d'application.  Ce n'est pas nécessaire pour l'application de conserver une référence à un objet de contexte d'opération de socket asynchrone après qu'il a été envoyé comme un paramètre à l'une des méthodes d'opération de socket asynchrone.  Il restera référencé jusqu'à ce que le rappel d'exécution soit retourné.  Toutefois il est avantageux d'application de conserver la référence à l'objet de contexte afin qu'elle puisse être réutilisée pour une future opération de socket asynchrone.  
  
## Voir aussi  
 <xref:System.Net.Sockets.Socket?displayProperty=fullName>   
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=fullName>   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Exemple de technologie de performances de socket](http://go.microsoft.com/fwlink/?LinkID=179570)
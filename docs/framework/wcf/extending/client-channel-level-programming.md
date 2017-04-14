---
title: "Programmation au niveau du canal client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Programmation au niveau du canal client
Cette rubrique décrit comment écrire une application cliente [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sans utiliser la classe <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName> et son modèle objet associé.  
  
## Envoi des messages  
 Pour pouvoir envoyer des messages, puis recevoir et traiter les réponses, vous devez procéder comme suit :  
  
1.  Créez une liaison.  
  
2.  Générez une fabrication de canal.  
  
3.  Créez un canal.  
  
4.  Envoyez une demande et lisez la réponse.  
  
5.  Fermez tous les objets de canal.  
  
#### Création d'une liaison  
 À l'instar de la procédure de réception de messages \(consultez [Programmation de service au niveau du canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)\), la première étape pour envoyer des messages consiste à créer une liaison.Cet exemple crée une nouvelle liaison <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> et ajoute <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName> à sa collection Elements.  
  
#### Génération de ChannelFactory  
 Au lieu de créer <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=fullName>, nous créons cette fois <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName> en appelant <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=fullName> sur la liaison où le paramètre de type est <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=fullName>.Les écouteurs de canal sont utilisés par le côté qui attend les messages entrants et les fabrications de canaux le sont par le côté qui initialise la communication pour créer un canal.À l'instar des écouteurs de canal, les fabrications de canaux doivent d'abord être ouvertes avant de pouvoir être utilisées.  
  
#### Création d'un canal  
 Nous appelons ensuite <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=fullName> pour créer <xref:System.ServiceModel.Channels.IRequestChannel>.Cet appel prend l'adresse du point de terminaison avec lequel nous souhaitons communiquer en utilisant le nouveau canal créé.Après avoir capté un canal, nous appelons Open sur celui\-ci afin qu'il soit prêt pour la communication.Selon la nature du transport, cet appel à Open peut initialiser une connexion avec le point de terminaison cible ou peut ne rien faire du tout sur le réseau.  
  
#### Envoi d'une demande et lecture de la réponse  
 Une fois un canal ouvert, nous pouvons créer un message et utiliser la méthode Request du canal pour envoyer la demande et attendre le retour de la réponse.Cette méthode retourne un message de réponse permettant de connaître la réponse du point de terminaison.  
  
#### Fermeture des objets  
 Pour éviter la fuite des ressources, nous fermons les objets utilisés dans les communications lorsqu'ils ne sont plus nécessaires.  
  
 L'exemple de code suivant illustre un client de base utilisant la fabrication de canal pour envoyer un message et lire la réponse.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
---
title: "Utilisation des outils de d&#233;veloppement WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Utilisation des outils de d&#233;veloppement WCF
Cette section décrit les outils de développement [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] qui peuvent vous aider à développer votre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Vous pouvez utiliser les modèles [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] comme base pour générer rapidement votre propre service, puis utiliser l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour déboguer et tester votre service.  Ces outils offrent un cycle de débogage et de test rapide et transparent tout en supprimant l'obligation de se limiter à un modèle d'hébergement à un stade précoce.  
  
## Outils WCF Developer  
 [Modèles Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Vous pouvez utiliser les modèles d'élément et de projet [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour générer rapidement des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et des applications s'y rapportant.  
  
 [Hôte de service WCF \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(WcfSvcHost.exe\) vous permet de lancer le débogueur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] \(F5\) pour héberger et tester automatiquement un service que vous avez implémenté.  Vous pouvez ensuite tester le service à l'aide du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) ou de votre propre client, afin de rechercher et de résoudre les erreurs potentielles.  
  
 [Client test WCF \(WcfTestClient.exe\)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) est un outil GUI qui permet d'entrer des paramètres de types arbitraires, d'envoyer ces entrées au service et d'afficher la réponse que le service renvoie.  Il offre des conditions de test de service transparentes lorsqu'il est associé à l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 [Génération de classes de type de données à partir de XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Les données XML stockées dans le presse\-papiers peuvent être collées dans une page de codes.  Les classes définies dans les données sont converties en types de codes.  
  
## Utilisation des outils sans privilège d'administrateur  
 Pour permettre aux utilisateurs qui ne disposent pas de privilèges d'administrateur de développer des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], une liste de contrôle d'accès \(ACL, Access Control List\) est créée pour l'espace de noms http:\/\/\+:8731\/Design\_Time\_Addresses pendant l'installation de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  La liste ACL a la valeur \(UI\), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur.  Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux modèles WCF ou WF d'envoyer et de recevoir des données dans leur configuration par défaut.  Elle permet également aux utilisateurs d'utiliser l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(wcfSvcHost.exe\) sans leur accorder de privilèges d'administrateur.  
  
 Vous pouvez modifier l'accès à l'aide de l'outil Netsh.exe dans [!INCLUDE[wv](../../../includes/wv-md.md)] par le biais du compte d'administrateur supérieur.  L'utilisation de Netsh.exe est illustrée dans l'exemple suivant.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Netsh.exe, consultez [Utilisation de l'outil Netsh.exe et des commutateurs de ligne de commandes](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## Voir aussi  
 [Modèles Visual Studio WCF](../../../docs/framework/wcf/wcf-vs-templates.md)   
 [Hôte de service WCF \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)   
 [Client test WCF \(WcfTestClient.exe\)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
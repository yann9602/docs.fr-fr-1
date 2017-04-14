---
title: "Meilleures pratiques dans un environnement de confiance partielle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Meilleures pratiques dans un environnement de confiance partielle
Cette rubrique décrit les meilleures pratiques lors de l'exécution de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans un environnement de confiance partielle.  
  
## Sérialisation  
 Appliquez les pratiques suivantes lors de l'utilisation du <xref:System.Runtime.Serialization.DataContractSerializer> dans une application de confiance partielle.  
  
-   Tous les types sérialisables doivent être marqués explicitement avec l'attribut `[DataContract]`.Les techniques suivantes ne sont pas prises en charge dans un environnement de confiance partielle :  
  
-   Marquage des classes à sérialiser avec le <xref:System.SerializableAttribute>.  
  
-   L'implémentation de l'interface <xref:System.Runtime.Serialization.ISerializable> pour permettre à une classe de contrôler son processus de sérialisation.  
  
### Utilisation de DataContractSerializer  
  
-   Tous les types marqués avec l'attribut `[DataContract]` doivent être publics.Les types non publics ne peuvent pas être sérialisés dans un environnement de confiance partielle.  
  
-   Tous les membres `[DataContract]` dans un type `[DataContract]` sérialisable doivent être publics.Un type avec un `[DataMember]` non public ne peut pas être sérialisé dans un environnement de confiance partielle.  
  
-   Les méthodes qui gèrent des événements de sérialisation \(telles que `OnSerializing`, `OnSerialized`, `OnDeserializing`et `OnDeserialized`\) doivent être déclarées comme publiques.Toutefois, les implémentations explicites et implicites de <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> sont prises en charge.  
  
-   Les types `[DataContract]` implémentés dans les assemblys marqués avec <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ne doivent pas effectuer d'actions relatives à la sécurité dans le constructeur de type, étant donné que <xref:System.Runtime.Serialization.DataContractSerializer> n'appelle pas le constructeur de l'objet instancié récemment pendant la désérialisation.En particulier, les techniques de sécurité courantes suivantes doivent être évitées pour les types `[DataContract]` :  
  
-   Tenter de restreindre l'accès de confiance partielle en rendant le constructeur du type interne ou privé.  
  
-   Restreindre l'accès au type en ajoutant un `[LinkDemand]` au constructeur du type.  
  
-   Supposer que du fait de l'instanciation correcte de l'objet, les contrôles de validation appliqués par le constructeur ont réussi.  
  
### Utilisation de IXmlSerializable  
 Les meilleures pratiques suivantes s'appliquent aux types qui implémentent <xref:System.Xml.Serialization.IXmlSerializable> et sont sérialisés à l'aide du <xref:System.Runtime.Serialization.DataContractSerializer> :  
  
-   Les implémentations de méthode statique <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> doivent être `public`.  
  
-   Les méthodes d'instance qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable> doivent être `public`.  
  
## Utilisation de WCF à partir d'un code de plateforme d'un niveau de confiance suffisant qui autorise les appels d'appelants d'un niveau de confiance partiel  
 Le modèle de sécurité de confiance partielle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suppose que tout appelant d'une méthode ou propriété publique [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute dans le contexte de sécurité d'accès du code \(CAS\) de l'application d'hébergement.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suppose également qu'un seul contexte de sécurité des applications existe pour chaque <xref:System.AppDomain>, et que ce contexte est établi à l'heure de création <xref:System.AppDomain> par un hôte approuvé \(par exemple, par un appel à <xref:System.AppDomain.CreateDomain%2A> ou par le Gestionnaire d'application ASP.NET\).  
  
 Ce modèle de sécurité s'applique aux applications écrites par l'utilisateur qui ne peuvent pas déclarer des autorisations CAS supplémentaires, telles que l'exécution du code utilisateur dans une application ASP.NET de confiance moyenne.Toutefois, le code de plateforme d'un niveau de confiance total \(par exemple, un assembly tiers installé dans le cache d'assembly global et qui accepte des appels de code de niveau de confiance partiel\) doit faire preuve de prudence lors de l'appel dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] au nom d'une application de confiance partielle pour éviter d'introduire des failles de sécurité au niveau de l'application.  
  
 Le code de confiance totale doit éviter de modifier le jeu d'autorisations CAS du thread actuel \(en appelant la méthode <xref:System.Security.PermissionSet.Assert%2A><xref:System.Security.PermissionSet.PermitOnly%2A> ou <xref:System.Security.PermissionSet.Deny%2A>\) avant d'appeler les API de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de la part du code d'un niveau de confiance partiel.La déclaration ou le refus, ou toute création d'un contexte d'autorisation spécifique au thread qui est indépendant du contexte de sécurité au niveau de l'application, peut entraîner un comportement imprévu.Selon l'application, ce comportement peut provoquer des failles de sécurité au niveau de l'application.  
  
 Le code qui appelle dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un contexte d'autorisation spécifique au thread doit être prêt à gérer les situations suivantes susceptibles de se produire :  
  
-   Le contexte de sécurité spécifique au thread ne peut pas être maintenu pour la durée de l'opération, ce qui provoque des exceptions de sécurité potentielles.  
  
-   Le code [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] interne, ainsi que tous les rappels fournis par l'utilisateur, peuvent s'exécuter dans un contexte de sécurité différent de celui dans lequel l'appel a été initialisé à l'origine.Ces contextes sont les suivants :  
  
    -   Le contexte d'autorisation d'application.  
  
    -   Tout contexte d'autorisation spécifique au thread créé précédemment par d'autres threads utilisateur utilisés pour appeler dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pendant la durée de vie du <xref:System.AppDomain> en cours d'exécution.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] garantit que le code d'un niveau de confiance partiel ne peut pas obtenir des autorisations de confiance totale sauf si ces autorisations sont déclarées par un composant d'un niveau de confiance total avant d'appeler dans les API publiques de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Toutefois, il ne garantit pas que les effets de la déclaration de la confiance totale sont isolés d'un thread, d'une opération ou d'une action utilisateur en particulier.  
  
 La meilleure pratique consiste à éviter de créer le contexte d'autorisation spécifique au thread en appelant <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A> ou <xref:System.Security.PermissionSet.Deny%2A>.Au lieu de cela, accordez ou refusez le privilège à l'application, afin qu'aucune méthode <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A> ou <xref:System.Security.PermissionSet.PermitOnly%2A> ne soit requise.  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Xml.Serialization.IXmlSerializable>
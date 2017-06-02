---
title: "UriTemplate Table, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# UriTemplate Table, exemple
La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire permettant d'utiliser un ensemble d'instances d'`UriTemplate`.Les URI \(Uniform Resource Identifier\) spécifiques peuvent être mis en correspondance avec tous les modèles de la table de manière efficace, et les données associées au modèle mis en correspondance peuvent être récupérées.  
  
 Cet exemple présente les concepts clés suivants relatifs à la classe `UriTemplateTable` :  
  
-   Syntaxe d'instanciation de `UriTemplateTable`.  
  
-   Remplissage de `UriTemplateTable` avec un jeu de paires clé\/valeur.  
  
-   Mise en correspondance d'un URI candidat avec la table à l'aide de <xref:System.UriTemplateTable.MatchSingle%2A>.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## Voir aussi  
 [UriTemplate Table Dispatcher](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)   
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
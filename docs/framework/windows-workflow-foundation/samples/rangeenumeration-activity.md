---
title: "Activit&#233; RangeEnumeration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Activit&#233; RangeEnumeration
Cet exemple montre comment créer une activité personnalisée qui itère au sein d'une collection de nombres. Le tableau suivant détaille les fichiers principaux inclus dans l'exemple.  
  
|Nom de fichier|Description|  
|--------------------|-----------------|  
|RangeEnumeration.cs|Définit une activité personnalisée nommée `RangeEnumeration` qui substitue la classe <xref:System.Activities.NativeActivity> et effectue une boucle sur une série de nombres.|  
|RangeEnumerationSample.cs|Application cliente qui utilise l'activité `RangeEnumeration` pour itérer au sein d'une collection de nombres.|  
  
 Le tableau suivant détaille les propriétés de l'activité `RangeEnumeration`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|Start|Entier auquel démarrer la boucle.|  
|Stop|Entier auquel arrêter la boucle.|  
|Step|Spécifie le volume d'itération à chaque fois.|  
|Body|Spécifie le code à exécuter pendant chaque itération.|  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution RangeEnumeration.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`  
  
## Voir aussi
---
title: "Glossaire Windows Workflow Foundation pour .NET Framework&#160;4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WF [WF], glossaire"
  - "Windows Workflow Foundation [WF], glossaire"
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: 259
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 259
---
# Glossaire Windows Workflow Foundation pour .NET Framework&#160;4.5
Les termes suivants sont utilisés dans la documentation de Windows Workflow Foundation.  
  
## Termes  
  
|Terme|Définition|  
|-----------|----------------|  
|activité|Unité de comportement de programme dans Windows Workflow Foundation.Les activités simples peuvent être décomposées en activités plus complexes.|  
|action d'activité|Structure de données utilisée pour exposer des rappels pour l'exécution de workflows et d'activités.|  
|argument|Définit le flux de données dans et hors d'une activité.Chaque argument a une direction spécifiée : dans, hors ou dans\/hors.Ils représentent les paramètres d'entrée, de sortie et d'entrée\/sortie de l'activité.|  
|signet|Point auquel une activité peut être suspendue et attendre sa reprise.|  
|compensation|Groupe d'actions conçu pour annuler ou atténuer l'effet d'un travail précédent.|  
|corrélation|Mécanisme d'acheminement de messages vers une instance de service ou de workflow.|  
|expression|Construction qui accepte un ou plusieurs arguments, effectue une opération sur ces arguments et retourne une valeur unique.Les expressions peuvent être utilisées partout où une activité peut l'être également.|  
|organigramme|Paradigme de modélisation célèbre qui représente les composants d'un programme sous forme de symboles liés entre eux par des flèches directionnelles.Dans .NET Framework 4, les workflows peuvent être modélisés en tant qu'organigrammes à l'aide de l'activité Flowchart.|  
|processus de longue durée|Unité d'exécution d'un programme qui ne retourne pas les résultats immédiatement et peut se prolonger au\-delà de plusieurs redémarrages du système.|  
|persistance|Enregistrement de l'état d'un workflow ou d'un service sur un support durable, afin qu'il puisse être déchargé de la mémoire ou récupéré après une défaillance du système.|  
|ordinateur d'état|Paradigme de modélisation célèbre qui représente les composants d'un programme en tant qu'états individuels liés entre eux par des transitions d'état pilotés par événement.Les workflows peuvent être modélisés comme ordinateurs d'état à l'aide de l'activité StateMachine.|  
|substance|Représente un groupe de signets associés sous un identificateur commun et permet au runtime de prendre des décisions quant à la validité ou à la date de prochaine validité de la reprise d'un signet particulier.|  
|convertisseur de type|Un type CLR peut être associé à un ou plusieurs types System.ComponentModel.TypeConverter dérivés qui permettent la conversion d'instances de type CLR en instances d'autres types.Un convertisseur de type est associé à un type CLR à l'aide de l'attribut System.ComponentModel.TypeConverterAttribute.Un TypeConverterAttribute peut être spécifié directement sur le type CLR ou sur une propriété.Un convertisseur de type spécifié sur une propriété a toujours priorité sur un convertisseur de type spécifié sur le type CLR de la propriété.|  
|variable|Représente le stockage de certaines données qui doivent être enregistrées en vue d'un accès ultérieur.|  
|workflow|Activité unique ou arborescence d'activités appelée par un processus hôte.|  
|XAML|Langage XAML \(eXtensible Application Markup Language\)|
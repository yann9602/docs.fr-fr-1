---
title: "Utilisation d&#39;une activit&#233; personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Utilisation d&#39;une activit&#233; personnalis&#233;e
Les activités qui dérivent de la classe <xref:System.Activities.Activity> ou de ses sous\-classes peuvent être composées de plus grands workflows, ou créées directement dans le code.Cette rubrique explique comment utiliser des activités personnalisées dans les workflows créés dans le code ou dans le concepteur.  
  
> [!NOTE]
>  Les activités personnalisées peuvent être utilisées dans le même projet que celui dans lequel elles sont définies, tant que l'activité personnalisée et l'activité qui l'utilise sont compilées \(c.\-à\-d.,chargées par un type d'instanciation généré par le processus de génération\). Si l'activité de référence est chargée dynamiquement \(par exemple,en utilisant ActivityXAMLServices\), alors l'assembly référencé doit être inséré dans un autre projet, ou le code XAML généré par le concepteur doit être modifié manuellement à cet effet.  
  
#### Utilisation d'une activité personnalisée dans un projet de workflow  
  
1.  Ajoutez une référence du projet hôte au projet de bibliothèque d'activités qui contient l'activité personnalisée.  
  
2.  Générez la solution.  
  
3.  Pour utiliser l'activité personnalisée dans le concepteur, recherchez l'activité personnalisée dans la boîte à outils, puis faites glisser l'activité sur l'aire du concepteur.  
  
4.  Pour utiliser l'activité personnalisée dans le code, ajoutez une instruction Using qui fait référence au projet d'activité personnalisée, puis passez une nouvelle instance de l'activité à <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
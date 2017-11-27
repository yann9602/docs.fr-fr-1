---
title: "Utilisation d'une activité personnalisée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e534f9a3e8d0a7d675e43bc03266e4863f95d45d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-custom-activity"></a>Utilisation d'une activité personnalisée
Les activités qui dérivent de la classe <xref:System.Activities.Activity> ou de ses sous-classes peuvent être composées de plus grands workflows, ou créées directement dans le code. Cette rubrique explique comment utiliser des activités personnalisées dans les workflows créés dans le code ou dans le concepteur.  
  
> [!NOTE]
>  Activités personnalisées peuvent être utilisées dans le même projet que celui dans lequel elles sont définies, tant que l’activité personnalisée et l’activité qui l’utilise sont compilées (c.-à-d. chargé par un type d’instanciation généré par le processus de génération) si l’activité de référence est chargée. dynamique (par exemple, en utilisant ActivityXAMLServices), puis l’assembly référencé doit être placé dans un autre projet ou le code XAML généré par le concepteur doit être modifié manuellement pour activer cette option.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Utilisation d'une activité personnalisée dans un projet de workflow  
  
1.  Ajoutez une référence du projet hôte au projet de bibliothèque d'activités qui contient l'activité personnalisée.  
  
2.  Générez la solution.  
  
3.  Pour utiliser l'activité personnalisée dans le concepteur, recherchez l'activité personnalisée dans la boîte à outils, puis faites glisser l'activité sur l'aire du concepteur.  
  
4.  Pour utiliser l'activité personnalisée dans le code, ajoutez une instruction Using qui fait référence au projet d'activité personnalisée, puis passez une nouvelle instance de l'activité à <xref:System.Activities.WorkflowInvoker.Invoke%2A>.

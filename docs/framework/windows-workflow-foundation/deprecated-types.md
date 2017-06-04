---
title: "Deprecated types in Windows Workflow Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Deprecated types in Windows Workflow Foundation
Dans le .NET 4, l'équipe de workflow a mis à disposition un nouveau au moteur de workflow dans l'espace de noms <xref:System.Activities>.  Avec la version du .NET 4.5 bêta, la majorité des types dans les espaces de noms « WF 3 » <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel> et <xref:System.Workflow.Runtime> sont marqués comme étant obsolètes.  
  
## Espaces de noms et outils obsolètes  
 Les assemblys suivants ont un ou plusieurs types publics qui seront déconseillés :  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 Par conséquent, les clients qui utilisent les API WF 3 déconseillées rencontreront des avertissements de génération avec un message similaire au suivant :  
  
  **Avertissement BC40000 : X est obsolète : Les types WF 3 sont déconseillés.  Utilisez plutôt WF 4.**  Nous allons supprimer les types du .NET Framework dans une version ultérieure, mais nous n'avons pas encore déterminé cette plage de temps \(pas dans la version 4.5\).  Cette étape nous permet de communiquer notre direction à nos clients et leur laisse le temps de migrer vers le nouveau modèle WF4.  Naturellement, nous continuerons à prendre en charge ces types WF 3 dans le cadre de la [Politique de support Microsoft](http://aka.ms/MicrosoftSupportLifecycle).  Les applications WF3 existantes s'exécutent sans problème sur le .NET 4.5, et [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] prend en charge les solutions WF3 nouvelles et existantes.  
  
 Les types liés aux règles dans l'espace de noms <xref:System.Workflow.Activities.Rules>, qui n'ont pas été remplacés dans WF 4.5, n'ont pas été déconseillés.  
  
 Les clients qui souhaitent migrer leurs applications vers WF 4 trouveront de l'aide dans les articles [Conseils de migration pour Windows Workflow 4](http://aka.ms/WF4MigrationGuidance) sur MSDN et dans le [Kit de migration WF 4](http://aka.ms/WF4MigrationKit) sur le site [WF Codeplex](http://aka.ms/WFCodeplex).
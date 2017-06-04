---
title: "T&#226;che 1 : cr&#233;er une nouvelle application Windows Presentation Foundation. | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# T&#226;che 1 : cr&#233;er une nouvelle application Windows Presentation Foundation.
Dans cette tâche, vous allez créer une application [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] vide à l'aide du modèle Visual Studio d'application WPF, et ajouter des références aux assemblys de workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] appropriés.  
  
### Pour créer le projet d'application WPF  
  
1.  Ouvrez [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], puis dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C\#** ou **Visual Basic** dans le volet **Modèles installés** situé sur le côté gauche.Si le langage de votre choix n'apparaît pas, recherchez\-le sous **Autres langages**.  
  
3.  Dans le volet **Modèles installés**, sélectionnez **Windows**.  
  
4.  Dans du volet supérieur, vérifiez que **.NET Framework 4.0** \(valeur par défaut\) a été sélectionné dans la zone de liste déroulante, puis sélectionnez **Application WPF**.  
  
5.  Définissez **HostingApplication** comme nom du projet en bas de la fenêtre.  
  
6.  Définissez **RehostingTheDesigner** comme nom de la solution.  
  
7.  Cliquez sur **OK** pour créer le projet d'application.[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] crée une interface utilisateur WPF de base de votre application et inclut le code XAML et les fichiers code\-behind appropriés.  
  
8.  Ajoutez des références aux assemblys **WorkflowModel**.Pour ce faire, dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **HostingApplication**, puis sélectionnez **Ajouter une référence**.  
  
9. Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l'onglet **.NET**, maintenez la touche CTRL enfoncée, sélectionnez les assemblys suivants, puis cliquez sur **OK** :  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Cliquez sur **OK**.  
  
11. Pour en savoir plus sur l'hébergement de la zone de conception du Workflow Designer, consultez [Tâche 2 : héberger le Workflow Designer](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md).  
  
## Voir aussi  
 [Réhébergement du Workflow Designer](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [Tâche 2 : héberger le Workflow Designer](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)
---
title: "R&#233;glage des performances dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGridView (contrôle Windows Forms), réglage des performances"
  - "réglage des performances, grilles de données"
  - "performances, DataGridView (contrôle)"
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# R&#233;glage des performances dans le contr&#244;le DataGridView Windows Forms
Lorsque vous travaillez avec de grandes quantités de données, le contrôle `DataGridView` peut consommer une grande quantité de mémoire si vous ne l'utilisez pas avec soin.  Sur les clients disposant d'une mémoire limitée, vous pouvez économiser des ressources mémoire en renonçant à des fonctionnalités qui coûtent cher en mémoire.  Vous pouvez également gérer entièrement ou partiellement les tâches de récupération et de maintenance des données vous\-même en utilisant le mode virtuel pour personnaliser l'utilisation de la mémoire pour votre scénario.  
  
## Dans cette section  
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser le contrôle `DataGridView` d'une manière qui évite d'inutiles pénalités d'utilisation et de performance de la mémoire lorsque vous travaillez avec de grandes quantités de données.  
  
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser le mode virtuel pour compléter ou remplacer le mécanisme de liaison de données standard.  
  
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Décrit comment implémenter des gestionnaires pour plusieurs événements de mode virtuel.  Décrit également comment implémenter la reprise au niveau de la ligne et valider pour les modifications d'utilisateur.  
  
 [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Décrit comment charger les données à la demande, ce qui est utile lorsque vous avez plus de données à afficher que peut en stocker la mémoire du client.  
  
## Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit de la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Fournit de la documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
## Voir aussi  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
---
title: "Meilleures pratiques pour le contr&#244;le TableLayoutPanel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "dimensionnement automatique"
  - "AutoSize (propriété), TableLayoutPanel (contrôle)"
  - "meilleures pratiques, TableLayoutPanel (contrôle)"
  - "contrôles (Windows Forms), dimensionner"
  - "formulaires, meilleures pratiques"
  - "disposition (Windows Forms)"
  - "disposition (Windows Forms), meilleures pratiques"
  - "disposition (Windows Forms), AutoSize"
  - "dimensionner, automatique"
  - "TableLayoutPanel (contrôle Windows Forms), meilleures pratiques"
  - "TableLayoutPanel (contrôle Windows Forms), AutoSize (comportement)"
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Meilleures pratiques pour le contr&#244;le TableLayoutPanel
Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> fournit des fonctionnalités de disposition puissantes que vous devez considérer avec soin avant de les utiliser sur vos Windows Forms.  
  
## Recommandations  
 Les recommandations suivantes vous aideront à utiliser au mieux le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
### Utilisation visée  
 Utilisez le contrôle <xref:System.Windows.Forms.TableLayoutPanel> avec modération.  Vous ne devez pas l'utiliser dans toutes les situations qui requièrent une disposition redimensionnable.  La liste suivante décrit les dispositions qui bénéficient le plus de l'utilisation du contrôle <xref:System.Windows.Forms.TableLayoutPanel> :  
  
-   Dispositions dans lesquelles il existe plusieurs parties du formulaire qui se redimensionnent proportionnellement les unes par rapport aux autres.  
  
-   Les dispositions qui seront modifiées ou générées dynamiquement au moment de l'exécution, comme les formulaires de saisie de données qui ont des champs utilisateur personnalisables ou qui sont ajoutés ou soustraits selon des préférences.  
  
-   Dispositions qui doivent rester à une taille fixe totale.  Par exemple, vous pouvez avoir une boîte de dialogue qui doit rester inférieure à que 800 x 600, mais vous devez prendre en charge des chaînes localisées.  
  
 La liste suivante décrit les dispositions qui ne bénéficient pas beaucoup de l'utilisation du contrôle <xref:System.Windows.Forms.TableLayoutPanel> :  
  
-   Les formulaires de saisie de données simples avec une unique colonne d'étiquettes et une unique colonne de zones de saisie de texte.  
  
-   Les formulaires avec une seule grande zone d'affichage qui doit remplir tout l'espace disponible lorsqu'un redimensionnement se produit.  Un formulaire qui affiche un contrôle <xref:System.Windows.Forms.PropertyGrid> unique en est un exemple.  Dans ce cas, utilisez l'ancrage car aucun élément ne doit se développer lorsque le formulaire est redimensionné.  
  
 Choisissez avec soin les contrôles qui doivent figurer dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Si vous avez assez de place pour que votre texte augmente de 30 % à l'aide de l'ancrage, envisagez d'utiliser uniquement la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.  Si vous pouvez estimer l'espace requis par votre disposition, il est plus facile d'utiliser les propriétés <xref:System.Windows.Forms.Control.Dock%2A> et <xref:System.Windows.Forms.Control.Anchor%2A> que d'estimer les détails de l'espace restant et du comportement de <xref:System.Windows.Forms.Control.AutoSize%2A>.  
  
 En général, lorsque vous concevez votre disposition avec le contrôle <xref:System.Windows.Forms.TableLayoutPanel>, faites en sorte que cette conception soit aussi simple que possible.  
  
### Utilisation de la fenêtre Structure du document  
 La fenêtre Structure du document vous offre une arborescence de votre disposition que vous pouvez utiliser pour manipuler l'ordre de plan et les relations parent\/enfant de vos contrôles.  Dans le menu **Affichage**, sélectionnez **Autres fenêtres**, puis **Structure du document**.  
  
### Évitez l'imbrication  
 Évitez d'imbriquer d'autres contrôles <xref:System.Windows.Forms.TableLayoutPanel> dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Le débogage des dispositions imbriquées peut être difficile.  
  
### Évitez l'héritage visuel  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> ne prend pas en charge l'héritage visuel dans le Concepteur Windows Forms.  Un contrôle <xref:System.Windows.Forms.TableLayoutPanel> dans une classe dérivée apparaît comme « verrouillé » au moment du design.  
  
## Voir aussi  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 <xref:System.Windows.Forms.FlowLayoutPanel>
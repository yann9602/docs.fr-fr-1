---
title: "Comment : ajouter des données personnalisées aux données de l'encre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f266f3c98ca64c80ccbb669a1cc646321754579f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-add-custom-data-to-ink-data"></a>Comment : ajouter des données personnalisées aux données de l'encre
Vous pouvez ajouter des données personnalisées à encre sera enregistré lors de l’encre est enregistré sous la forme d’encre sérialisée format ISF (Ink).  Vous pouvez enregistrer les données personnalisées pour le <xref:System.Windows.Ink.DrawingAttributes>, le <xref:System.Windows.Ink.StrokeCollection>, ou <xref:System.Windows.Ink.Stroke>.  La possibilité d’enregistrer des données personnalisées sur trois objets vous donne la possibilité de choisir le meilleur emplacement pour enregistrer les données.  Ces trois classes utilisent des méthodes semblables pour stocker et accéder aux données personnalisées.  
  
 Seuls les types suivants peuvent être enregistrés en tant que données personnalisées :  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter et récupérer des données personnalisées à partir d’un <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 L’exemple suivant crée une application qui affiche un <xref:System.Windows.Controls.InkCanvas> et deux boutons.  Le bouton, `switchAuthor`, Active deux stylets être utilisé par deux auteurs.  Le bouton `changePenColors` modifie la couleur de chaque trait sur la <xref:System.Windows.Controls.InkCanvas> en fonction de l’auteur.  L’application définit deux <xref:System.Windows.Ink.DrawingAttributes> des objets et ajoute une propriété personnalisée à chacun d’eux qui indique l’auteur ayant dessiné le <xref:System.Windows.Ink.Stroke>.  Lorsque l’utilisateur clique sur `changePenColors`, l’application modifie l’apparence du trait selon la valeur de la propriété personnalisée.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]

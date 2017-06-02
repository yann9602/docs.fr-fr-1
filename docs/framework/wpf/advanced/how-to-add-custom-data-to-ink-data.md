---
title: "Comment&#160;: ajouter des donn&#233;es personnalis&#233;es aux donn&#233;es de l&#39;encre | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "données de l'encre, ajouter des données personnalisées"
  - "InkCanvas, afficher"
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: ajouter des donn&#233;es personnalis&#233;es aux donn&#233;es de l&#39;encre
Vous pouvez ajouter des données personnalisées à l'encre. Ces dernières sont enregistrées lorsque l'encre est enregistrée au format ISF.  Vous pouvez enregistrer les données personnalisées dans <xref:System.Windows.Ink.DrawingAttributes>, <xref:System.Windows.Ink.StrokeCollection>ou <xref:System.Windows.Ink.Stroke>.  Le fait de pouvoir enregistrer des données personnalisées sur trois objets vous donne la possibilité de choisir le meilleur emplacement pour enregistrer les données.  Ces trois classes utilisent des méthodes semblables pour le stockage et l'accès aux données personnalisées.  
  
 Seuls les types suivants peuvent être enregistrés en tant que données personnalisées :  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>\[\]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>\[\]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>\[\]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>\[\]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>\[\]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>\[\]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>\[\]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>\[\]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>\[\]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>\[\]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>\[\]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>\[\]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>\[\]  
  
## Exemple  
 L'exemple suivant montre comment ajouter et récupérer des données personnalisées depuis un <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 L'exemple suivant crée une application qui affiche un <xref:System.Windows.Controls.InkCanvas> et deux boutons.  Le bouton `switchAuthor` active deux stylets qui doivent être utilisés par deux auteurs différents.  Le bouton `changePenColors` modifie la couleur de chaque trait dans le <xref:System.Windows.Controls.InkCanvas> selon l'auteur.  L'application définit deux objets <xref:System.Windows.Ink.DrawingAttributes> et ajoute une propriété personnalisée pour indiquer l'auteur ayant dessiné le <xref:System.Windows.Ink.Stroke>.  Lorsque l'utilisateur clique sur `changePenColors`, l'application modifie l'apparence du trait selon la valeur de la propriété personnalisée.  
  
 [!code-xml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
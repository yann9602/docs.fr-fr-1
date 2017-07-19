---
title: "Comment&#160;: cloner une imprimante | Microsoft Docs"
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
  - "cloner des files d'attente à l'impression"
  - "cloner des imprimantes"
  - "files d'attente à l'impression"
  - "files d'attente à l'impression, cloner"
  - "imprimantes, cloner"
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cloner une imprimante
La plupart des entreprises achètent, à un moment donné, plusieurs imprimantes du même modèle.  En général, celles\-ci sont toutes installées avec des paramètres de configuration quasiment identiques.  L'installation de chaque imprimante peut représenter une perte de temps et constitue un risque d'erreur.  L'espace de noms <xref:System.Printing.IndexedProperties?displayProperty=fullName> et la classe <xref:System.Printing.PrintServer.InstallPrintQueue%2A> qui sont exposés avec [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] permettent d'installer instantanément n'importe quel nombre de files d'attente à l'impression supplémentaires qui sont des clones de la file d'attente à l'impression existante.  
  
## Exemple  
 Dans l'exemple ci\-dessous, une deuxième file d'attente à l'impression est clonée d'une file d'attente à l'impression existante.  Le nom, l'emplacement, le port et l'état partagé de la deuxième diffèrent de ceux de la première.  Les étapes principales de cette procédure sont les suivantes.  
  
1.  Créez un objet <xref:System.Printing.PrintQueue> pour l'imprimante existante qui va être clonée.  
  
2.  Créez un <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> à partir du <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> du <xref:System.Printing.PrintQueue>.  La propriété <xref:System.Collections.DictionaryEntry.Value%2A> de chaque entrée dans ce dictionnaire est un objet de l'un des types dérivés de <xref:System.Printing.IndexedProperties.PrintProperty>.  Il existe deux façons de définir la valeur d'une entrée dans ce dictionnaire.  
  
    -   Utilisez les méthodes **Supprimer** et <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> du dictionnaire pour supprimer l'entrée, puis l'ajouter de nouveau avec la valeur souhaitée.  
  
    -   Utilisez la méthode <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> du dictionnaire.  
  
     L'exemple suivant illustre les deux méthodes.  
  
3.  Créez un objet <xref:System.Printing.IndexedProperties.PrintBooleanProperty>, puis affectez « IsShared » à sa propriété <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> et la valeur `true` à sa propriété <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A>.  
  
4.  Utilisez l'objet <xref:System.Printing.IndexedProperties.PrintBooleanProperty> en tant que valeur de l'entrée « IsShared » de <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>.  
  
5.  Créez un objet <xref:System.Printing.IndexedProperties.PrintStringProperty>, puis affectez la valeur « ShareName » à sa propriété <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> et affectez une <xref:System.String> appropriée à sa propriété <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>.  
  
6.  Utilisez l'objet <xref:System.Printing.IndexedProperties.PrintStringProperty> en tant que valeur de l'entrée « ShareName » de <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>.  
  
7.  Créez un autre objet <xref:System.Printing.IndexedProperties.PrintStringProperty>, puis affectez la valeur « Location » à sa propriété <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> et affectez une <xref:System.String> appropriée à sa propriété <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>.  
  
8.  Utilisez le deuxième objet <xref:System.Printing.IndexedProperties.PrintStringProperty> en tant que valeur de l'entrée « Location » de <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>.  
  
9. Créez un tableau de <xref:System.String>s.  Chaque élément correspond au nom d'un port sur le serveur.  
  
10. Utilisez <xref:System.Printing.PrintServer.InstallPrintQueue%2A> pour installer la nouvelle imprimante avec les nouvelles valeurs.  
  
 Voici un exemple :  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## Voir aussi  
 <xref:System.Printing.IndexedProperties>   
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Collections.DictionaryEntry>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)
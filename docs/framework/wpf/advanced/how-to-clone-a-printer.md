---
title: "Comment : cloner une imprimante"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43a08faf27186bde85dd12f027034f759378debf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clone-a-printer"></a>Comment : cloner une imprimante
La plupart des entreprises, à un moment donné, d’acheter plusieurs imprimantes du même modèle. En général, celles-ci sont toutes installées avec les paramètres de configuration quasiment identiques. L’installation de chaque imprimante peut prendre du temps et sujet aux erreurs. Le <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> espace de noms et le <xref:System.Printing.PrintServer.InstallPrintQueue%2A> classe qui sont exposés avec [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] rend possible d’installer instantanément n’importe quel nombre de files d’attente à l’impression supplémentaires qui sont clonés à partir d’une file d’attente d’impression existant.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple ci-dessous, une deuxième file d’attente d’impression est cloné à partir d’une file d’attente d’impression existant. La seconde est différente de la première uniquement dans son nom, un emplacement, un port et un état partagé. Voici les principales étapes de cette opération.  
  
1.  Créer un <xref:System.Printing.PrintQueue> objet pour l’imprimante existante qui va être clonée.  
  
2.  Créer un <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> à partir de la <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> de la <xref:System.Printing.PrintQueue>. Le <xref:System.Collections.DictionaryEntry.Value%2A> propriété de chaque entrée de ce dictionnaire est un objet de l’un des types dérivés de <xref:System.Printing.IndexedProperties.PrintProperty>. Il existe deux façons de définir la valeur d’une entrée dans ce dictionnaire.  
  
    -   Utiliser le dictionnaire **supprimer** et <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> méthodes pour supprimer l’entrée, puis ajoutez-le de nouveau avec la valeur souhaitée.  
  
    -   Utiliser le dictionnaire <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> (méthode).  
  
     L’exemple suivant illustre deux façons.  
  
3.  Créer un <xref:System.Printing.IndexedProperties.PrintBooleanProperty> et définissez son <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> « IsShared » et ses <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> à `true`.  
  
4.  Utilisez le <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objet à la valeur de la <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>de « IsShared » entrée.  
  
5.  Créer un <xref:System.Printing.IndexedProperties.PrintStringProperty> et définissez son <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> « ShareName » et ses <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> aux <xref:System.String>.  
  
6.  Utilisez le <xref:System.Printing.IndexedProperties.PrintStringProperty> objet à la valeur de la <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>d’entrée « ShareName ».  
  
7.  Création d’une autre <xref:System.Printing.IndexedProperties.PrintStringProperty> et définissez son <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> à « Emplacement » et ses <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> aux <xref:System.String>.  
  
8.  Utilisez la deuxième <xref:System.Printing.IndexedProperties.PrintStringProperty> objet à la valeur de la <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>d’entrée « Location ».  
  
9. Créer un tableau de <xref:System.String>s. Chaque élément est le nom d’un port sur le serveur.  
  
10. Utilisez <xref:System.Printing.PrintServer.InstallPrintQueue%2A> pour installer la nouvelle imprimante avec les nouvelles valeurs.  
  
 Il est un exemple ci-dessous.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)

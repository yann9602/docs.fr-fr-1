---
title: "Comment : gérer des erreurs et des exceptions qui se produisent avec Databinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a78612fc17eea01508dcba9247ece68be2e19a76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>Comment : gérer des erreurs et des exceptions qui se produisent avec Databinding
Souvent, les exceptions et les erreurs surviennent quand vous liez des objets métier sous-jacents aux contrôles. Vous pouvez intercepter ces erreurs et ces exceptions, puis récupérer ou bien passer des informations d'erreur à l'utilisateur en gérant l'événement <xref:System.Windows.Forms.Binding.BindingComplete> pour un composant <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource> ou <xref:System.Windows.Forms.CurrencyManager>.  
  
## <a name="example"></a>Exemple  
 Cet exemple de code montre comment gérer les erreurs et les exceptions qui se produisent pendant une opération de liaison de données. Il montre comment intercepter des erreurs en gérant l'événement <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> des objets <xref:System.Windows.Forms.Binding>. Pour intercepter les erreurs et les exceptions en gérant cet événement, vous devez activer la mise en forme de la liaison. Vous pouvez activer la mise en forme quand la liaison est construite ou ajoutée à la collection de liaison, ou bien en définissant la propriété <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> sur `true`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 Quand le code s'exécute et qu'une chaîne vide est entrée pour le nom du composant ou qu'une valeur inférieure à 100 est entrée pour le numéro du composant, un message s'affiche. Ceci est la conséquence de la gestion de l'événement <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> pour ces liaisons de zone de texte.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [BindingSource, composant](../../../../docs/framework/winforms/controls/bindingsource-component.md)

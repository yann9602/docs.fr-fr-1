---
title: "Comment : créer un Windows Form redimensionnable pour l'entrée de données"
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
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51e844dc49f75e2f27ad5bbaf9176e71f6e3388a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Comment : créer un Windows Form redimensionnable pour l'entrée de données
Une bonne disposition répond correctement aux modifications des dimensions de son formulaire parent. Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.TableLayoutPanel> pour organiser la disposition de votre formulaire afin de redimensionner et de positionner vos contrôles de façon cohérente à mesure que les dimensions du formulaire changent. Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> est également utile quand des modifications du contenu de vos contrôles entraîne une modification de la disposition. Vous pouvez effectuer les tâches décrites dans cette procédure dans l'environnement Visual Studio.  Consultez également [Procédure pas à pas : création d’un Windows Form redimensionnable pour l’entrée de données](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> pour générer une disposition qui répond correctement quand l'utilisateur redimensionne le formulaire. Il illustre également une disposition qui répond correctement à la localisation.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Guide pratique pour créer une présentation Windows Forms qui répond bien à la localisation](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Expérience utilisateur Microsoft Windows, Recommandations officielles à destination des développeurs et des concepteurs d’interfaces utilisateur. Redmond, WA: Microsoft Press, 1999. (USBN : 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)

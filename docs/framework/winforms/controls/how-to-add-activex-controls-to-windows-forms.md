---
title: "Comment : ajouter des contrôles ActiveX aux Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 940dd21fc48c23ce623280aab2c487db5810057c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Comment : ajouter des contrôles ActiveX aux Windows Forms
Alors que le Concepteur Windows Forms est optimisé pour héberger des contrôles Windows Forms, vous pouvez également insérer des contrôles ActiveX aux Windows Forms.  
  
> [!CAUTION]
>  Il existe des limitations de performances pour les Windows Forms lorsque des contrôles ActiveX leur sont ajoutés.  
  
 Avant d’ajouter des contrôles ActiveX à votre formulaire, vous devez les ajouter à la boîte à outils. Pour plus d’informations, consultez [des composants COM, boîte de dialogue Personnaliser la boîte à outils](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Pour ajouter un contrôle ActiveX à votre Windows Form  
  
-   Double-cliquez sur le contrôle dans la boîte à outils.  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]Ajoute toutes les références au contrôle de votre projet. Pour plus d’informations sur les éléments à prendre en compte lors de l’utilisation de contrôles ActiveX aux Windows Forms, consultez [considérations sur l’hébergement d’un contrôle ActiveX dans un Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  L’importateur de contrôles ActiveX Windows Forms (AxImp.exe) crée des arguments d’événement d’un type différent que prévu lors de l’importation de bibliothèques de liens dynamiques ActiveX. Les arguments créés par AxImp.exe sont semblables à ce qui suit : `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, lorsque `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` est attendu. N’oubliez pas que cette anomalie n’empêche pas le code de fonctionner normalement. Pour plus d’informations, consultez [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Comparaison des contrôles et des objets programmables dans divers langages et bibliothèques](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)

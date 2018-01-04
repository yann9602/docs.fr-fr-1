---
title: "Utilisation de contrôles WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c14da85b377b3ef80d6accbc8b0319959a75bcd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-wpf-controls"></a>Utilisation de contrôles WPF
Vous pouvez utiliser des contrôles Windows Presentation Foundation (WPF) dans vos applications Windows Forms. Bien que ces deux technologies d’affichage différentes, elles interagissent sans heurts.  
  
 Le Concepteur Windows Forms fournit un environnement de conception visuelle pour l’hébergement de contrôles Windows Presentation Foundation. Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>. Ce contrôle permet le contrôle WPF de participer à la disposition du formulaire et de recevoir des messages de clavier et souris. Au moment du design, vous pouvez organiser les <xref:System.Windows.Forms.Integration.ElementHost> contrôler tout comme vous le feriez pour n’importe quel contrôle Windows Forms.  
  
 Vous pouvez également utiliser des contrôles Windows Forms dans vos applications WPF. Pour plus d’informations, consultez [Concepteur WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour copier et coller un contrôle ElementHost au moment du design](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Montre comment copier un contrôle Windows Presentation Foundation sur un Windows Form.  
  
 [Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Montre comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour organiser les contrôles Windows Presentation Foundation.  
  
 [Procédure pas à pas : modification des propriétés d'un élément WPF hébergé au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Affiche le workflow entre le Concepteur Windows Forms et le [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] pour modifier des propriétés sur les contrôles WPF.  
  
 [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Montre comment créer un contrôle Windows Presentation Foundation pour une utilisation dans vos applications Windows Forms.  
  
 [Procédure pas à pas : copier-coller d'un contrôle ElementHost dans d'autres Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Montre comment copier un contrôle Windows Presentation Foundation à partir d’un Windows Form à un autre.  
  
 [Procédure pas à pas : assignation du contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Montre comment sélectionner les types de contrôles Windows Presentation Foundation que vous souhaitez afficher sur votre formulaire.  
  
 [Procédure pas à pas : application de styles au contenu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Affiche le workflow entre le Concepteur Windows Forms et le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pour appliquer des styles à des contrôles Windows Presentation Foundation.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Décrit une classe que vous pouvez utiliser pour héberger des contrôles Windows Presentation Foundation dans vos applications Windows Forms.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Décrit une classe que vous pouvez utiliser pour héberger des contrôles Windows Forms dans votre application Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Décrit l’interopérabilité entre les technologies Windows Presentation Foundation et Windows Forms.  
  
 [Concepteur WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 Explique comment concevoir des contrôles Windows Presentation Foundation dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].

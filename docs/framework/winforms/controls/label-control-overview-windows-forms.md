---
title: "Vue d'ensemble du contrôle Label (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f68642eb5f996722097976e042006afbf366ae39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="label-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Label (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Label> contrôles sont utilisés pour afficher du texte ou des images qui ne sont pas modifiables par l’utilisateur. Ils sont utilisés pour identifier des objets sur un formulaire — pour décrire ce que fait un contrôle lorsque vous cliquez dessus, par exemple, ou pour afficher des informations en réponse à un événement d’exécution ou dans votre application. Par exemple, vous pouvez utiliser des étiquettes pour ajouter des légendes pour les zones de texte, zones de liste, zones de liste déroulante et ainsi de suite. Vous pouvez également écrire du code qui modifie le texte affiché par une étiquette en réponse aux événements au moment de l’exécution. Par exemple, si votre application prend quelques minutes pour traiter une modification, vous pouvez afficher un message d’état de traitement dans une étiquette.  
  
## <a name="working-with-the-label-control"></a>Utilisation du contrôle Label  
 Étant donné que le <xref:System.Windows.Forms.Label> contrôle ne peut pas recevoir le focus, il peut également être utilisé pour créer des touches d’accès rapide pour d’autres contrôles. Une clé d’accès permet à un utilisateur de sélectionner l’autre contrôle en appuyant sur la touche ALT et la clé d’accès. Pour plus d’informations, consultez [création de clés d’accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : créer des touches d’accès rapide avec le contrôle Label Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).  
  
 La légende affichée dans l’étiquette est contenue dans le <xref:System.Windows.Forms.Label.Text%2A> propriété. Le <xref:System.Windows.Forms.Label.TextAlign%2A> propriété vous permet de définir l’alignement du texte dans l’étiquette. Pour plus d’informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Label>  
 [Guide pratique pour dimensionner un contrôle Label Windows Forms en fonction de son contenu](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [Guide pratique pour créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)

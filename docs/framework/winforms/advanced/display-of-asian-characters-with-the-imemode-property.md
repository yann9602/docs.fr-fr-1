---
title: "Affichage des caractères asiatiques avec la propriété ImeMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Affichage des caractères asiatiques avec la propriété ImeMode
Le <xref:System.Windows.Forms.Control.ImeMode%2A> propriété est utilisée par les formulaires et les contrôles pour forcer un mode spécifique pour un éditeur de méthode d’entrée (IME). L’IME est un composant essentiel pour écrire en chinois, japonais et coréen, étant donné que ces systèmes d’écriture ont plus de caractères que ce que vous pouvez coder pour un clavier standard. Par exemple, vous voulez autoriser uniquement des caractères ASCII dans une zone de texte particulière. Dans ce cas, vous pouvez définir le <xref:System.Windows.Forms.Control.ImeMode%2A> propriété <xref:System.Windows.Forms.ImeMode> et les utilisateurs seulement sera en mesure d’entrer des caractères ASCII pour cette zone de texte particulière. La valeur par défaut de la <xref:System.Windows.Forms.Control.ImeMode%2A> propriété <xref:System.Windows.Forms.ImeMode>, de sorte que si vous définissez la propriété d’un formulaire, tous les contrôles sur le formulaire héritent ce paramètre. Pour plus d’informations, consultez <xref:System.Windows.Forms.Control.ImeMode%2A> ) et <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Voir aussi  
 [Globalisation des Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)

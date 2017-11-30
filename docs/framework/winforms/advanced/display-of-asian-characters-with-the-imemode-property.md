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
ms.openlocfilehash: 4ba86b0c1343d84e65f0e3f9ff48a09b3a80a27a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="71708-102">Affichage des caractères asiatiques avec la propriété ImeMode</span><span class="sxs-lookup"><span data-stu-id="71708-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="71708-103">Le <xref:System.Windows.Forms.Control.ImeMode%2A> propriété est utilisée par les formulaires et les contrôles pour forcer un mode spécifique pour un éditeur de méthode d’entrée (IME).</span><span class="sxs-lookup"><span data-stu-id="71708-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="71708-104">L’IME est un composant essentiel pour écrire en chinois, japonais et coréen, étant donné que ces systèmes d’écriture ont plus de caractères que ce que vous pouvez coder pour un clavier standard.</span><span class="sxs-lookup"><span data-stu-id="71708-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="71708-105">Par exemple, vous voulez autoriser uniquement des caractères ASCII dans une zone de texte particulière.</span><span class="sxs-lookup"><span data-stu-id="71708-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="71708-106">Dans ce cas, vous pouvez définir le <xref:System.Windows.Forms.Control.ImeMode%2A> propriété <xref:System.Windows.Forms.ImeMode> et les utilisateurs seulement sera en mesure d’entrer des caractères ASCII pour cette zone de texte particulière.</span><span class="sxs-lookup"><span data-stu-id="71708-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="71708-107">La valeur par défaut de la <xref:System.Windows.Forms.Control.ImeMode%2A> propriété <xref:System.Windows.Forms.ImeMode>, de sorte que si vous définissez la propriété d’un formulaire, tous les contrôles sur le formulaire héritent ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="71708-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="71708-108">Pour plus d’informations, consultez <xref:System.Windows.Forms.Control.ImeMode%2A> ) et <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="71708-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71708-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71708-109">See Also</span></span>  
 [<span data-ttu-id="71708-110">Globalisation des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71708-110">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)

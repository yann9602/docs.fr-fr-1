---
title: "Comment : imprimer un Windows Form"
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
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9149b90317036c7c62c5fca3056bb697df56e543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="676e3-102">Comment : imprimer un Windows Form</span><span class="sxs-lookup"><span data-stu-id="676e3-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="676e3-103">Dans le cadre du processus de développement, vous généralement souhaiterez imprimer une copie de votre Windows Form.</span><span class="sxs-lookup"><span data-stu-id="676e3-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="676e3-104">L’exemple de code suivant montre comment imprimer une copie de l’écran actuel à l’aide de la <xref:System.Drawing.Graphics.CopyFromScreen%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="676e3-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="676e3-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="676e3-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="676e3-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="676e3-106">Compiling the Code</span></span>  
 <span data-ttu-id="676e3-107">Il s’agit d’un exemple de code complet qui contient un `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="676e3-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="676e3-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="676e3-108">Robust Programming</span></span>  
 <span data-ttu-id="676e3-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="676e3-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="676e3-110">Vous n’avez pas l’autorisation d’accéder à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="676e3-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="676e3-111">Aucune imprimante n’est installée.</span><span class="sxs-lookup"><span data-stu-id="676e3-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="676e3-112">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="676e3-112">.NET Framework Security</span></span>  
 <span data-ttu-id="676e3-113">Pour exécuter cet exemple de code, vous devez disposer d’autorisation d’accéder à l’imprimante que vous utilisez avec votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="676e3-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676e3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="676e3-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="676e3-115">Guide pratique pour rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="676e3-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="676e3-116">Comment : imprimer des graphiques dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="676e3-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)

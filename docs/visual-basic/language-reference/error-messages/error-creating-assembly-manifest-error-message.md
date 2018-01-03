---
title: "Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="72c44-102">Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt;</span><span class="sxs-lookup"><span data-stu-id="72c44-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="72c44-103">Le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appelle Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste.</span><span class="sxs-lookup"><span data-stu-id="72c44-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="72c44-104">L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="72c44-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="72c44-105">Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué.</span><span class="sxs-lookup"><span data-stu-id="72c44-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="72c44-106">Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées.</span><span class="sxs-lookup"><span data-stu-id="72c44-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="72c44-107">Pour différer la signature d’un assembly, vous devez cocher la case **Différer la signature uniquement** et fournir un fichier de clé valide contenant des informations de clés publiques.</span><span class="sxs-lookup"><span data-stu-id="72c44-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="72c44-108">La clé privée n'est pas nécessaire quand la signature d'un assembly est différée.</span><span class="sxs-lookup"><span data-stu-id="72c44-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="72c44-109">Pour plus d’informations, consultez [Guide pratique pour signer un assembly avec un nom fort](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="72c44-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="72c44-110">**ID d’erreur :** BC30140</span><span class="sxs-lookup"><span data-stu-id="72c44-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72c44-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="72c44-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="72c44-112">Examinez le message d’erreur entre guillemets et consultez la rubrique [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="72c44-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="72c44-113">pour l’erreur AL1019 davantage d’explications et conseils</span><span class="sxs-lookup"><span data-stu-id="72c44-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="72c44-114">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="72c44-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c44-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72c44-115">See Also</span></span>  
 [<span data-ttu-id="72c44-116">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="72c44-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="72c44-117">Page Signature, Concepteur de projet</span><span class="sxs-lookup"><span data-stu-id="72c44-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="72c44-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="72c44-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="72c44-119">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="72c44-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)

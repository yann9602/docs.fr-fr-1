---
title: "Une référence a été créée pour l’assembly d’interopérabilité incorporé &#39; &lt;assembly1&gt;&#39; en raison d’une référence indirecte à cet assembly à partir d’assembly &#39;&lt; Assembly2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aaaa7460ade00ad4232807ce11ee125e270742bf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="13229-102">Une référence a été créée pour l’assembly d’interopérabilité incorporé &#39; &lt;assembly1&gt;&#39; en raison d’une référence indirecte à cet assembly à partir d’assembly &#39;&lt; Assembly2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="13229-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="13229-103">Une référence a été créée pour l’assembly d’interopérabilité incorporé '\<assembly1>' en raison d’une référence indirecte à cet assembly à partir de l’assembly '\<assembly2>'.</span><span class="sxs-lookup"><span data-stu-id="13229-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="13229-104">Modifiez la propriété 'Incorporer les types interop' pour l’un des assemblys.</span><span class="sxs-lookup"><span data-stu-id="13229-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="13229-105">Vous avez ajouté une référence à un assembly (assembly1) avec une valeur de propriété `Embed Interop Types` égale à `True`.</span><span class="sxs-lookup"><span data-stu-id="13229-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="13229-106">Cela indique au compilateur d’incorporer les informations de type interop à partir de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="13229-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="13229-107">Toutefois, le compilateur ne peut pas incorporer les informations de type interop à partir de cet assembly, car un autre assembly que vous avez référencé (assembly2) fait également référence à cet assembly (assembly1) et a la propriété `Embed Interop Types` définie sur `False`.</span><span class="sxs-lookup"><span data-stu-id="13229-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13229-108">L’affectation de la valeur `True` à la propriété `Embed Interop Types` d’une référence d’assembly revient à référencer l’assembly en utilisant l’option `/link` pour le compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="13229-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="13229-109">**ID d’erreur :** BC40059</span><span class="sxs-lookup"><span data-stu-id="13229-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="13229-110">Pour traiter cet avertissement</span><span class="sxs-lookup"><span data-stu-id="13229-110">To address this warning</span></span>  
  
-   <span data-ttu-id="13229-111">Pour incorporer des informations de type interop pour les deux assemblys, affectez la valeur `True` à la propriété `Embed Interop Types` de toutes les références à assembly1.</span><span class="sxs-lookup"><span data-stu-id="13229-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="13229-112">Pour supprimer cet avertissement, vous pouvez affecter à la propriété `Embed Interop Types` d’assembly1 la valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="13229-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="13229-113">Dans ce cas, les informations de type d’interopérabilité sont fournies par un assembly PIA (PIA).</span><span class="sxs-lookup"><span data-stu-id="13229-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13229-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13229-114">See Also</span></span>  
 [<span data-ttu-id="13229-115">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13229-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="13229-116">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="13229-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)

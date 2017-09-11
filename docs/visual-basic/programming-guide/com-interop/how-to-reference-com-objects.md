---
title: "Comment : référencer les objets COM à partir de Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5f7f1112161d9be995cc80378ad9dd95c522198d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="03f8c-102">Comment : référencer les objets COM à partir de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03f8c-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="03f8c-103">Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], ajouter des références aux objets COM qui possèdent des bibliothèques de types requiert la création d’un assembly d’interopérabilité pour la bibliothèque COM.</span><span class="sxs-lookup"><span data-stu-id="03f8c-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="03f8c-104">Les références aux membres de l’objet COM sont routées vers l’assembly d’interopérabilité et ensuite transmis à l’objet COM réel.</span><span class="sxs-lookup"><span data-stu-id="03f8c-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="03f8c-105">Les réponses de l’objet COM sont routées vers l’assembly d’interopérabilité et transmis à votre [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="03f8c-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span>  
  
 <span data-ttu-id="03f8c-106">Vous pouvez référencer un objet COM sans utiliser un assembly d’interopérabilité en incorporant les informations de type pour l’objet COM dans un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="03f8c-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="03f8c-107">Pour incorporer les informations de type, affectez le `Embed Interop Types` propriété `True` pour la référence à l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="03f8c-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="03f8c-108">Si vous compilez à l’aide du compilateur de ligne de commande, utilisez la `/link` option pour faire référence à la bibliothèque COM.</span><span class="sxs-lookup"><span data-stu-id="03f8c-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="03f8c-109">Pour plus d’informations, consultez [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="03f8c-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="03f8c-110">crée automatiquement des assemblys d’interopérabilité lorsque vous ajoutez une référence à une bibliothèque de types à partir de l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="03f8c-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="03f8c-111">Lorsque vous travaillez à partir de la ligne de commande, vous pouvez utiliser l’utilitaire Tlbimp pour créer manuellement des assemblys PIA.</span><span class="sxs-lookup"><span data-stu-id="03f8c-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="03f8c-112">Pour ajouter des références aux objets COM</span><span class="sxs-lookup"><span data-stu-id="03f8c-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="03f8c-113">Sur le **projet** menu, choisissez **ajouter une référence** puis cliquez sur le **COM** onglet dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="03f8c-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="03f8c-114">Sélectionnez le composant que vous souhaitez utiliser dans la liste des objets COM.</span><span class="sxs-lookup"><span data-stu-id="03f8c-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="03f8c-115">Pour simplifier l’accès à l’assembly d’interopérabilité, ajoutez une `Imports` en haut de la classe ou le module dans lequel vous allez utiliser l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="03f8c-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="03f8c-116">Par exemple, l’exemple de code suivant importe l’espace de noms `INKEDLib` pour les objets référencés dans la `Microsoft InkEdit Control 1.0` library.</span><span class="sxs-lookup"><span data-stu-id="03f8c-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     <span data-ttu-id="03f8c-117">[!code-vb[VbVbalrInterop numéro&40;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="03f8c-117">[!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span></span>  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="03f8c-118">Pour créer un assembly d’interopérabilité à l’aide de Tlbimp</span><span class="sxs-lookup"><span data-stu-id="03f8c-118">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="03f8c-119">Ajoutez l’emplacement de Tlbimp au chemin de recherche, si elle n’est pas déjà partie du chemin de recherche et que vous n’êtes pas actuellement dans le répertoire dans lequel il se trouve.</span><span class="sxs-lookup"><span data-stu-id="03f8c-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="03f8c-120">Appelez Tlbimp à partir d’une invite de commandes, en fournissant les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="03f8c-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="03f8c-121">Nom et l’emplacement de la DLL qui contient la bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="03f8c-121">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="03f8c-122">Nom et emplacement de l’espace de noms où les informations doivent être placées</span><span class="sxs-lookup"><span data-stu-id="03f8c-122">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="03f8c-123">Nom et emplacement de l’assembly d’interopérabilité cible</span><span class="sxs-lookup"><span data-stu-id="03f8c-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="03f8c-124">Le code suivant est fourni à titre d'exemple :</span><span class="sxs-lookup"><span data-stu-id="03f8c-124">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="03f8c-125">Vous pouvez utiliser Tlbimp pour créer des assemblys PIA pour les bibliothèques de types, même pour les objets COM non inscrits.</span><span class="sxs-lookup"><span data-stu-id="03f8c-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="03f8c-126">Toutefois, les objets COM référencés par les assemblys PIA doivent être inscrits correctement sur l’ordinateur sur lequel ils doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="03f8c-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="03f8c-127">Vous pouvez enregistrer un objet COM à l’aide de l’utilitaire Regsvr32 fourni avec le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="03f8c-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f8c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03f8c-128">See Also</span></span>  
 <span data-ttu-id="03f8c-129">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="03f8c-129">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="03f8c-130"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span><span class="sxs-lookup"><span data-stu-id="03f8c-130"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span></span>  
<span data-ttu-id="03f8c-131"> [Tlbexp.exe (exportateur de bibliothèques)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span><span class="sxs-lookup"><span data-stu-id="03f8c-131"> [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span></span>  
<span data-ttu-id="03f8c-132"> [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="03f8c-132"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="03f8c-133"> [Résolution des problèmes d’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span><span class="sxs-lookup"><span data-stu-id="03f8c-133"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span></span>  
<span data-ttu-id="03f8c-134"> [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="03f8c-134"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>

---
title: "Comment : référencer les objets COM à partir de Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a8ac167b40688b1d1116f148d0d5fd6afdcaada8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="6f0bd-102">Comment : référencer les objets COM à partir de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f0bd-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="6f0bd-103">Dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], ajouter des références aux objets COM qui possèdent des bibliothèques de types requiert la création d’un assembly d’interopérabilité pour la bibliothèque COM.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="6f0bd-104">Les références aux membres de l’objet COM sont routées vers l’assembly PIA et ensuite transmis à l’objet COM réel.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="6f0bd-105">Les réponses de l’objet COM sont routées vers l’assembly PIA et transférés vers votre [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="6f0bd-106">Vous pouvez référencer un objet COM sans utiliser un assembly d’interopérabilité en incorporant les informations de type pour l’objet COM dans un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="6f0bd-107">Pour incorporer les informations de type, affectez le `Embed Interop Types` propriété `True` pour la référence à l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="6f0bd-108">Si vous compilez à l’aide du compilateur de ligne de commande, utilisez la `/link` option pour faire référence à la bibliothèque COM.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="6f0bd-109">Pour plus d’informations, consultez [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="6f0bd-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6f0bd-110">crée automatiquement des assemblys d’interopérabilité lorsque vous ajoutez une référence à une bibliothèque de types à partir de l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="6f0bd-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="6f0bd-111">Lorsque vous travaillez à partir de la ligne de commande, vous pouvez utiliser l’utilitaire Tlbimp pour créer manuellement des assemblys PIA.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="6f0bd-112">Pour ajouter des références aux objets COM</span><span class="sxs-lookup"><span data-stu-id="6f0bd-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="6f0bd-113">Sur le **projet** menu, choisissez **ajouter une référence** puis cliquez sur le **COM** onglet dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="6f0bd-114">Sélectionnez le composant que vous souhaitez utiliser dans la liste des objets COM.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="6f0bd-115">Pour simplifier l’accès à l’assembly d’interopérabilité, ajoutez une `Imports` en haut de la classe ou le module dans lequel vous allez utiliser l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="6f0bd-116">Par exemple, l’exemple de code suivant importe l’espace de noms `INKEDLib` pour les objets référencés dans la `Microsoft InkEdit Control 1.0` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="6f0bd-117">Pour créer un assembly d’interopérabilité à l’aide de Tlbimp</span><span class="sxs-lookup"><span data-stu-id="6f0bd-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="6f0bd-118">Ajoutez l’emplacement de Tlbimp au chemin de recherche, si elle n’est pas déjà partie du chemin de recherche et vous n’êtes pas actuellement dans le répertoire où il se trouve.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="6f0bd-119">Appelez Tlbimp à partir d’une invite de commandes, en fournissant les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6f0bd-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="6f0bd-120">Nom et l’emplacement de la DLL qui contient la bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="6f0bd-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="6f0bd-121">Nom et l’emplacement de l’espace de noms dans lequel les informations doivent être placées</span><span class="sxs-lookup"><span data-stu-id="6f0bd-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="6f0bd-122">Nom et l’emplacement de l’assembly d’interopérabilité cible</span><span class="sxs-lookup"><span data-stu-id="6f0bd-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="6f0bd-123">Le code suivant est fourni à titre d'exemple :</span><span class="sxs-lookup"><span data-stu-id="6f0bd-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="6f0bd-124">Vous pouvez utiliser Tlbimp pour créer des assemblys PIA pour les bibliothèques de types, même pour les objets COM non inscrits.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="6f0bd-125">Toutefois, les objets COM référencés par les assemblys PIA doivent être correctement inscrit sur l’ordinateur sur lequel ils doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="6f0bd-126">Vous pouvez enregistrer un objet COM à l’aide de l’utilitaire Regsvr32 fourni avec le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="6f0bd-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f0bd-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f0bd-127">See Also</span></span>  
 [<span data-ttu-id="6f0bd-128">COM Interop</span><span class="sxs-lookup"><span data-stu-id="6f0bd-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="6f0bd-129">Tlbimp.exe (importateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="6f0bd-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="6f0bd-130">Tlbexp.exe (exportateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="6f0bd-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="6f0bd-131">Procédure pas à pas : implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="6f0bd-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="6f0bd-132">Dépannage des problèmes liés à l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="6f0bd-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="6f0bd-133">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="6f0bd-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)

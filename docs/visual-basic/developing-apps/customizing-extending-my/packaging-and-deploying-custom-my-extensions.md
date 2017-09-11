---
title: "Empaquetage et déploiement des extensions My (Visual Basic) personnalisé | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
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
ms.openlocfilehash: 81483722227873d1b145219ae5c4326d841ff876
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="20ab5-102">Empaquetage et déploiement des extensions My (Visual Basic) personnalisé</span><span class="sxs-lookup"><span data-stu-id="20ab5-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="20ab5-103">Visual Basic fournit un moyen facile pour vous permettre de déployer vos `My` extensions de l’espace de noms à l’aide de modèles Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20ab5-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="20ab5-104">Si vous créez un modèle de projet pour lequel votre `My` extensions font partie intégrante du nouveau type de projet, vous pouvez simplement inclure votre personnalisé `My` code d’extension avec le projet lors de l’exportation du modèle.</span><span class="sxs-lookup"><span data-stu-id="20ab5-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="20ab5-105">Pour plus d’informations sur l’exportation des modèles de projet, consultez [Comment : créer des modèles de projet](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).</span><span class="sxs-lookup"><span data-stu-id="20ab5-105">For more information about exporting project templates, see [How to: Create Project Templates](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).</span></span>  
  
 <span data-ttu-id="20ab5-106">Si votre personnalisé `My` extension est dans un seul fichier de code, vous pouvez exporter le fichier en tant que modèle d’élément que les utilisateurs peuvent ajouter à tout type de projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20ab5-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="20ab5-107">Vous pouvez ensuite personnaliser le modèle d’élément pour activer des fonctionnalités supplémentaires et le comportement de votre personnalisé `My` extension dans un projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20ab5-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="20ab5-108">Ces fonctionnalités sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="20ab5-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="20ab5-109">Permettre aux utilisateurs de gérer vos `My` extension à partir de la **Extensions My** page du Concepteur de projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20ab5-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="20ab5-110">Ajout automatique de vos `My` extension lorsqu’une référence à un assembly spécifié est ajoutée à un projet.</span><span class="sxs-lookup"><span data-stu-id="20ab5-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="20ab5-111">Masquer les `My` modèle d’élément extension dans le **ajouter un élément** afin qu’il n’est pas inclus dans la liste des éléments de projet de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="20ab5-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="20ab5-112">Cette rubrique explique comment empaqueter personnalisé `My` extension en tant que modèle d’élément caché pouvant être géré à partir de la **mes Extensions** page du Concepteur de projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20ab5-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="20ab5-113">Personnalisé `My` extension peut également être ajoutée automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet.</span><span class="sxs-lookup"><span data-stu-id="20ab5-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="20ab5-114">Créer une extension de l’espace de noms My</span><span class="sxs-lookup"><span data-stu-id="20ab5-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="20ab5-115">La première étape de création d’un package de déploiement personnalisé `My` extension consiste à créer l’extension comme un fichier de code unique.</span><span class="sxs-lookup"><span data-stu-id="20ab5-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="20ab5-116">Pour plus d’informations et des conseils sur la création d’un fichier personnalisé `My` extension, consultez [étendre le Namespace My dans Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="20ab5-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="20ab5-117">Exporter une extension de My namespace comme un modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="20ab5-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="20ab5-118">Une fois que vous avez un fichier de code qui inclut votre `My` extension de l’espace de noms, vous pouvez exporter le fichier de code comme un modèle d’élément Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20ab5-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="20ab5-119">Pour obtenir des instructions sur l’exportation d’un fichier comme un modèle d’élément Visual Studio, consultez [Comment : créer des modèles d’élément](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).</span><span class="sxs-lookup"><span data-stu-id="20ab5-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20ab5-120">Si votre `My` extension de l’espace de noms a une dépendance sur un assembly particulier, vous pouvez personnaliser votre modèle d’élément pour installer automatiquement votre `My` extension d’espace de noms lors de l’ajout d’une référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="20ab5-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="20ab5-121">Par conséquent, vous souhaitez exclure cette référence d’assembly lorsque vous exportez le fichier de code comme un modèle d’élément Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20ab5-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="20ab5-122">Personnaliser le modèle d’élément</span><span class="sxs-lookup"><span data-stu-id="20ab5-122">Customize the item template</span></span>  
 <span data-ttu-id="20ab5-123">Vous pouvez activer votre modèle d’élément à partir de la **mes Extensions** page du Concepteur de projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20ab5-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="20ab5-124">Vous pouvez également activer le modèle d’élément à ajouter automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet.</span><span class="sxs-lookup"><span data-stu-id="20ab5-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="20ab5-125">Pour activer ces personnalisations, vous serez ajouter un nouveau fichier, appelé le fichier CustomData, à votre modèle et puis ajoutez un nouvel élément au XML dans votre fichier .vstemplate.</span><span class="sxs-lookup"><span data-stu-id="20ab5-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="20ab5-126">Ajoutez le fichier CustomData</span><span class="sxs-lookup"><span data-stu-id="20ab5-126">Add the CustomData file</span></span>  
 <span data-ttu-id="20ab5-127">Le fichier CustomData est un fichier texte qui a l’extension de nom de fichier. CustomData (le nom de fichier peut être défini à toute valeur pertinente pour votre modèle) et contient le XML.</span><span class="sxs-lookup"><span data-stu-id="20ab5-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="20ab5-128">Le code XML du fichier CustomData demande à Visual Basic d’inclure votre `My` extension lorsque les utilisateurs utilisent le **mes Extensions** page du Concepteur de projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20ab5-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="20ab5-129">Vous pouvez éventuellement ajouter la `AssemblyFullName>` attribut à votre fichier XML CustomData.</span><span class="sxs-lookup"><span data-stu-id="20ab5-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="20ab5-130">Ce code indique à Visual Basic d’installer automatiquement votre personnalisé `My` extension lorsqu’une référence à un assembly donné est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="20ab5-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="20ab5-131">Vous pouvez utiliser n’importe quel éditeur de texte ou un éditeur XML pour créer le fichier CustomData et ajoutez-la au dossier de votre modèle d’élément compressé (fichier .zip).</span><span class="sxs-lookup"><span data-stu-id="20ab5-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="20ab5-132">Par exemple, le code XML suivant montre le contenu d’un fichier CustomData qui ajoute l’élément de modèle dans le dossier Extensions My d’un projet Visual Basic lorsqu’une référence à l’assembly Microsoft.VisualBasic.PowerPacks.Vs.dll est ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="20ab5-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="20ab5-133">Le fichier CustomData contient un `VBMyExtensionTemplate>` élément qui dispose des attributs répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="20ab5-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="20ab5-134">Attribut</span><span class="sxs-lookup"><span data-stu-id="20ab5-134">Attribute</span></span>|<span data-ttu-id="20ab5-135">Description</span><span class="sxs-lookup"><span data-stu-id="20ab5-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="20ab5-136">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="20ab5-136">Required.</span></span> <span data-ttu-id="20ab5-137">Identificateur unique pour l’extension.</span><span class="sxs-lookup"><span data-stu-id="20ab5-137">A unique identifier for the extension.</span></span> <span data-ttu-id="20ab5-138">Si l’extension qui possède cet ID a déjà été ajoutée au projet, l’utilisateur ne sera pas invité à ajouter à nouveau.</span><span class="sxs-lookup"><span data-stu-id="20ab5-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="20ab5-139">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="20ab5-139">Required.</span></span> <span data-ttu-id="20ab5-140">Un numéro de version du modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="20ab5-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="20ab5-141">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="20ab5-141">Optional.</span></span> <span data-ttu-id="20ab5-142">Nom d'assembly</span><span class="sxs-lookup"><span data-stu-id="20ab5-142">An assembly name.</span></span> <span data-ttu-id="20ab5-143">Lorsqu’une référence à cet assembly est ajoutée au projet, l’utilisateur sera invité à ajouter le `My` extension à partir de ce modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="20ab5-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="20ab5-144">Ajouter la \<CustomDataSignature > élément au fichier .vstemplate</span><span class="sxs-lookup"><span data-stu-id="20ab5-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="20ab5-145">Pour identifier votre modèle d’élément Visual Studio comme un `My` extension de l’espace de noms, vous devez également modifier le fichier .vstemplate pour votre modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="20ab5-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="20ab5-146">Vous devez ajouter un `<CustomDataSignature>` élément vers le `<TemplateData>` élément.</span><span class="sxs-lookup"><span data-stu-id="20ab5-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="20ab5-147">Le `<CustomDataSignature>` élément doit contenir le texte `Microsoft.VisualBasic.MyExtension`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="20ab5-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="20ab5-148">Vous ne pouvez pas modifier directement les fichiers dans un dossier compressé (fichier .zip).</span><span class="sxs-lookup"><span data-stu-id="20ab5-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="20ab5-149">Vous devez copier le fichier .vstemplate à partir du dossier compressé, le modifier et puis remplacez le fichier .vstemplate dans le dossier compressé par votre copie mise à jour.</span><span class="sxs-lookup"><span data-stu-id="20ab5-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="20ab5-150">L’exemple suivant montre le contenu d’un fichier .vstemplate qui a le `<CustomDataSignature>` élément ajouté.</span><span class="sxs-lookup"><span data-stu-id="20ab5-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
```  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a><span data-ttu-id="20ab5-151">Installer le modèle</span><span class="sxs-lookup"><span data-stu-id="20ab5-151">Install the template</span></span>  
 <span data-ttu-id="20ab5-152">Pour installer le modèle, vous pouvez copier le dossier compressé (fichier .zip) dans le dossier de modèles d’élément Visual Basic (par exemple, Mes Documents\Visual Studio 2008\Templates\Item terminée de base).</span><span class="sxs-lookup"><span data-stu-id="20ab5-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="20ab5-153">Vous pouvez également publier le modèle dans un fichier de programme d’installation de Visual Studio (.vsi).</span><span class="sxs-lookup"><span data-stu-id="20ab5-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ab5-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20ab5-154">See also</span></span>  
 <span data-ttu-id="20ab5-155">[Extension de l’espace de noms My dans Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="20ab5-155">[Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md) </span></span>  
<span data-ttu-id="20ab5-156"> [Extension du modèle d’application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span><span class="sxs-lookup"><span data-stu-id="20ab5-156"> [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md) </span></span>  
<span data-ttu-id="20ab5-157"> [Personnalisation des objets sont disponibles dans ma](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span><span class="sxs-lookup"><span data-stu-id="20ab5-157"> [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md) </span></span>  
<span data-ttu-id="20ab5-158"> [Extensions My, Page du Concepteur de projets](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="20ab5-158"> [My Extensions Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)</span></span>

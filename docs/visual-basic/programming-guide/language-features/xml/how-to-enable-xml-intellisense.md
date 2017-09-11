---
title: "Comment : activer XML IntelliSense dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e367016c93586ad34492628b6a4384a5ef1b6acd
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="05c95-102">Comment : activer XML IntelliSense dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05c95-102">How to: Enable XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="05c95-103">XML IntelliSense dans Visual Basic fournit le mot intégral des éléments définis dans un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="05c95-103">XML IntelliSense in Visual Basic provides word completion for elements that are defined in an XML schema.</span></span> <span data-ttu-id="05c95-104">Pour activer XML IntelliSense dans Visual Basic, vous devez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="05c95-104">To enable XML IntelliSense in Visual Basic, you must do the following:</span></span>  
  
1.  <span data-ttu-id="05c95-105">Obtenir le schéma XSD XML ou les fichiers pour les fichiers XML qui lit ou écrire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="05c95-105">Obtain the XML schema (XSD) file or files for the XML files that your application will read from or write to.</span></span>  
  
2.  <span data-ttu-id="05c95-106">Inclure les fichiers de schéma XML dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="05c95-106">Include the XML schema files in your project.</span></span>  
  
3.  <span data-ttu-id="05c95-107">Importez l’espace de noms cible ou les espaces de noms dans votre projet ou le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="05c95-107">Import the target namespace or namespaces into your code file or project.</span></span> <span data-ttu-id="05c95-108">Espace de noms cible est identifié par le `targetNamespace` ou `tns` attribut de votre schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="05c95-108">A target namespace is identified by the `targetNamespace` or `tns` attribute of your XSD schema.</span></span>  
  
     <span data-ttu-id="05c95-109">Pour importer un espace de noms cible, utilisez la `Imports` instruction, ou ajouter un espace de noms pour tous les fichiers de code dans un projet à l’aide de la **références** page du Concepteur de projets.</span><span class="sxs-lookup"><span data-stu-id="05c95-109">To import a target namespace, use the `Imports` statement, or add a namespace for all code files in a project by using the **References** page of the Project Designer.</span></span>  
  
 <span data-ttu-id="05c95-110">Pour plus d’informations sur les fonctionnalités de XML IntelliSense dans Visual Basic, consultez [XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span><span class="sxs-lookup"><span data-stu-id="05c95-110">For more information on the capabilities of XML IntelliSense in Visual Basic, see [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span></span> <span data-ttu-id="05c95-111">Pour plus d’informations sur l’importation d’espaces de noms XML, consultez [l’instruction Imports (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) ou [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="05c95-111">For more information on importing XML namespaces, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) or [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="05c95-112">![lien vers la vidéo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") pour obtenir une version vidéo de cette rubrique, consultez la page [vidéo Comment : activer XML IntelliSense dans Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466).</span><span class="sxs-lookup"><span data-stu-id="05c95-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Enable XML IntelliSense in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466).</span></span> <span data-ttu-id="05c95-113">Pour une démonstration vidéo connexe, consultez [comment activer XML IntelliSense and Use XML Namespaces ?](http://go.microsoft.com/fwlink/?LinkId=143035).</span><span class="sxs-lookup"><span data-stu-id="05c95-113">For a related video demonstration, see [How Do I Enable XML IntelliSense and Use XML Namespaces?](http://go.microsoft.com/fwlink/?LinkId=143035).</span></span>  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="05c95-114">Activer XML IntelliSense dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05c95-114">Enable XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="05c95-115">Si vous avez un fichier XML, mais vous n’avez pas un fichier de schéma XSD pour lui, dans SP1, vous pouvez créer un fichier de schéma XSD à l’aide de l’Assistant schéma XML vers.</span><span class="sxs-lookup"><span data-stu-id="05c95-115">If you have an XML file but you do not have an XSD schema file for it, in SP1 you can create an XSD schema file by using the XML to Schema Wizard.</span></span> <span data-ttu-id="05c95-116">Vous pouvez également utiliser l’inférence de schéma dans l’éditeur XML de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c95-116">You can also use schema inference in the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a><span data-ttu-id="05c95-117">Pour créer un fichier de schéma XSD pour un fichier XML à l’aide de l’Assistant schéma XML vers (SP1 requis)</span><span class="sxs-lookup"><span data-stu-id="05c95-117">To create an XSD schema file for an XML file by using the XML to Schema Wizard (requires SP1)</span></span>  
  
1.  <span data-ttu-id="05c95-118">Dans votre projet, cliquez sur **ajouter un nouvel élément** sur la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="05c95-118">In your project, click **Add New Item** on the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="05c95-119">Sélectionnez le **Xml au schéma** modèle d’élément à partir la **données** ou **éléments communs** catégories de modèles.</span><span class="sxs-lookup"><span data-stu-id="05c95-119">Select the **Xml to Schema** item template from either the **Data** or **Common Items** template categories.</span></span>  
  
3.  <span data-ttu-id="05c95-120">Fournissez un nom de fichier pour le fichier XSD ou les fichiers qui seront stockées dans le jeu de schémas déduits et puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="05c95-120">Provide a file name for the XSD file or files that the inferred schema set will be stored in, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="05c95-121">Dans le **déduire un schéma XML défini à partir de documents XML** fenêtre, ajoutez un ou plusieurs documents XML pour déduire le jeu de schémas XML.</span><span class="sxs-lookup"><span data-stu-id="05c95-121">In the **Infer XML Schema set from XML documents** window, add one or more XML documents to infer the XML schema set from.</span></span>  
  
    -   <span data-ttu-id="05c95-122">Pour ajouter des fichiers texte contenant des documents XML à l’aide de l’Explorateur de fichiers, cliquez sur **à partir du fichier**.</span><span class="sxs-lookup"><span data-stu-id="05c95-122">To add text files that contain XML documents by using File Explorer, click **Add from File**.</span></span>  
  
    -   <span data-ttu-id="05c95-123">Pour ajouter un document XML à partir d’une adresse HTTP, cliquez sur **à partir du Web**.</span><span class="sxs-lookup"><span data-stu-id="05c95-123">To add an XML document from an HTTP address, click **Add from Web**.</span></span>  
  
    -   <span data-ttu-id="05c95-124">Pour copier ou taper le contenu d’un document XML dans l’Assistant, cliquez sur **entrer ou coller du XML**.</span><span class="sxs-lookup"><span data-stu-id="05c95-124">To copy or type the contents of an XML document into the wizard, click **Type or paste XML**.</span></span>  
  
5.  <span data-ttu-id="05c95-125">Lorsque vous avez spécifié toutes les sources de document XML à partir de laquelle vous souhaitez déduire le jeu de schémas XML, cliquez sur **OK** déduire le schéma XML défini.</span><span class="sxs-lookup"><span data-stu-id="05c95-125">When you have specified all the XML document sources from which you want to infer the XML schema set, click **OK** to infer the XML schema set.</span></span> <span data-ttu-id="05c95-126">Le jeu de schémas est enregistré dans votre dossier de projet dans un ou plusieurs fichiers XSD.</span><span class="sxs-lookup"><span data-stu-id="05c95-126">The schema set is saved in your project folder in one or more XSD files.</span></span> <span data-ttu-id="05c95-127">(Pour chaque espace de noms XML dans le schéma, un fichier est créé.)</span><span class="sxs-lookup"><span data-stu-id="05c95-127">(For each XML namespace in the schema, a file is created.)</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a><span data-ttu-id="05c95-128">Pour créer un fichier de schéma XSD pour un fichier XML à l’aide de l’inférence de schéma dans l’éditeur XML de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05c95-128">To create an XSD schema file for an XML file by using schema inference in the Visual Studio XML Editor</span></span>  
  
1.  <span data-ttu-id="05c95-129">Modifiez le fichier XML dans le Concepteur XML de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05c95-129">Edit the XML file in the Visual Studio XML Designer.</span></span>  
  
2.  <span data-ttu-id="05c95-130">Lorsque le curseur se trouve dans le fichier XML, le **XML** menu s’affiche.</span><span class="sxs-lookup"><span data-stu-id="05c95-130">When the cursor is somewhere in the XML file, the **XML** menu appears.</span></span> <span data-ttu-id="05c95-131">Cliquez sur **Create Schema** sur la **XML** menu.</span><span class="sxs-lookup"><span data-stu-id="05c95-131">Click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="05c95-132">Un fichier XSD est créé à partir du schéma XSD déduit à partir du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="05c95-132">An XSD file is created from XSD schema inferred from the XML file.</span></span>  
  
3.  <span data-ttu-id="05c95-133">Enregistrez le fichier de schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="05c95-133">Save the XSD schema file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05c95-134">Différents schémas XSD peuvent être déduits à partir de plusieurs documents XML conçus pour avoir le même schéma.</span><span class="sxs-lookup"><span data-stu-id="05c95-134">Different XSD schemas might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="05c95-135">Cela peut se produire lorsque des éléments et attributs particuliers sont trouvées dans un fichier XML et pas dans un autre, ou lorsque les éléments sont inclus dans un ordre différent, par exemple.</span><span class="sxs-lookup"><span data-stu-id="05c95-135">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="05c95-136">Vous devez examiner les schémas XSD déduits d’exhaustivité et la précision lorsque vous utilisez l’inférence de schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="05c95-136">You should review inferred XSD schemas for completeness and accuracy when you use XSD schema inference.</span></span>  
  
#### <a name="to-include-an-xsd-schema-file"></a><span data-ttu-id="05c95-137">Pour inclure un fichier de schéma XSD</span><span class="sxs-lookup"><span data-stu-id="05c95-137">To include an XSD schema file</span></span>  
  
-   <span data-ttu-id="05c95-138">Par défaut, vous ne voyez pas de fichiers XSD dans les projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="05c95-138">By default, you cannot see XSD files in Visual Basic projects.</span></span> <span data-ttu-id="05c95-139">Si votre fichier XSD est déjà inclus dans les dossiers de votre projet, cliquez sur le **afficher tous les fichiers** bouton **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="05c95-139">If your XSD file is already included in the folders for your project, click the **Show All Files** button in **Solution Explorer**.</span></span> <span data-ttu-id="05c95-140">Localisez le fichier XSD dans **l’Explorateur de solutions**, cliquez sur le fichier, puis cliquez sur **inclure le fichier dans le projet**.</span><span class="sxs-lookup"><span data-stu-id="05c95-140">Locate the XSD file in **Solution Explorer**, right-click the file, and click **Include File in Project**.</span></span>  
  
-   <span data-ttu-id="05c95-141">Si votre fichier XSD n’est pas déjà partie de votre projet, dans **l’Explorateur de solutions**, cliquez sur le dossier dans lequel vous souhaitez stocker le fichier XSD, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="05c95-141">If your XSD file is not already part of your project, in **Solution Explorer**, right-click the folder in which you want to store the XSD file, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="05c95-142">Recherchez votre fichier XSD, puis cliquez **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="05c95-142">Locate your XSD file and then click **Add**.</span></span>  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a><span data-ttu-id="05c95-143">Pour importer un espace de noms XML dans un fichier de code</span><span class="sxs-lookup"><span data-stu-id="05c95-143">To import an XML namespace in a code file</span></span>  
  
1.  <span data-ttu-id="05c95-144">Identifiez l’espace de noms cible de schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="05c95-144">Identify the target namespace from your XSD schema.</span></span>  
  
2.  <span data-ttu-id="05c95-145">Au début du fichier de code, ajoutez une `Imports` instruction pour l’espace de noms XML cible, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="05c95-145">At the beginning of the code file, add an `Imports` statement for the target XML namespace, as shown in the following example.</span></span>  
  
     <span data-ttu-id="05c95-146">[!code-vb[VbXMLSamples n °&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="05c95-146">[!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span></span>  
  
     <span data-ttu-id="05c95-147">Pour importer un espace de noms XML en tant que l’espace de noms par défaut, autrement dit, l’espace de noms est appliqué aux éléments XML et les attributs qui n’ont pas un préfixe d’espace de noms, ajoutez un `Imports` instruction pour l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="05c95-147">To import an XML namespace as the default namespace, that is, the namespace that is applied to XML elements and attributes that do not have a namespace prefix, add an `Imports` statement for the target default XML namespace.</span></span> <span data-ttu-id="05c95-148">Ne spécifiez pas un préfixe d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="05c95-148">Do not specify a namespace prefix.</span></span> <span data-ttu-id="05c95-149">Voici un exemple d’un `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="05c95-149">Following is an example of an `Imports` statement.</span></span>  
  
     <span data-ttu-id="05c95-150">[!code-vb[VbXmlSamples&#50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="05c95-150">[!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span></span>  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a><span data-ttu-id="05c95-151">Pour importer un espace de noms XML pour tous les fichiers dans un projet</span><span class="sxs-lookup"><span data-stu-id="05c95-151">To import an XML namespace for all files in a project</span></span>  
  
1.  <span data-ttu-id="05c95-152">Un espace de noms XML importé dans un fichier de code s’applique à ce fichier de code uniquement.</span><span class="sxs-lookup"><span data-stu-id="05c95-152">An XML namespace imported in a code file applies to that code file only.</span></span> <span data-ttu-id="05c95-153">Pour importer un espace de noms XML qui s’applique à tous les fichiers de code dans un projet, ouvrez le Concepteur de projets en double-cliquant sur **mon projet** dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="05c95-153">To import an XML namespace that applies to all code files in a project, open the Project Designer by double-clicking **My Project** in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="05c95-154">Sur le **références** sous l’onglet du **espaces de noms importés** , tapez l’espace de noms cible XML sous la forme d’une déclaration d’espace de noms XML complète (par exemple, `<xmlns: ns="http://sampleNamespace">`).</span><span class="sxs-lookup"><span data-stu-id="05c95-154">On the **References** tab, in the **Imported namespaces** box, type the target XML namespace in the form of a full XML namespace declaration (for example, `<xmlns: ns="http://sampleNamespace">`).</span></span> <span data-ttu-id="05c95-155">Si l’espace de noms XML cible ne spécifie pas un préfixe d’espace de noms, l’espace de noms sera l’espace de noms XML par défaut pour le projet.</span><span class="sxs-lookup"><span data-stu-id="05c95-155">If the target XML namespace does not specify a namespace prefix, the namespace will be the default XML namespace for the project.</span></span>  
  
3.  <span data-ttu-id="05c95-156">Cliquez sur **ajouter une importation utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="05c95-156">Click **Add User Import**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c95-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05c95-157">See Also</span></span>  
 <span data-ttu-id="05c95-158">[Imports, instruction (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="05c95-158">[Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="05c95-159"> [Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="05c95-159"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="05c95-160"> [XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span><span class="sxs-lookup"><span data-stu-id="05c95-160"> [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span></span>


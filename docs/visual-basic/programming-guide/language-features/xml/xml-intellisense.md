---
title: XML IntelliSense dans Visual Basic | Documents Microsoft
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
- Visual Basic code, XML
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
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
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 9a3c6f923bc9458997c388d4cf74ca113265a8cc
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017

---
# <a name="xml-intellisense-in-visual-basic"></a><span data-ttu-id="87f50-102">XML IntelliSense dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87f50-102">XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="87f50-103">L’éditeur de Code Visual Basic inclut des fonctionnalités IntelliSense pour XML qui offrent une saisie semi-automatique de mots pour les éléments définis dans un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="87f50-103">The Visual Basic Code Editor includes IntelliSense features for XML that provide word completion for elements defined in an XML schema.</span></span> <span data-ttu-id="87f50-104">Si vous incluez un fichier de définition de schéma XML (XSD) dans votre projet et importer l’espace de noms cible du schéma à l’aide de la `Imports` instruction, l’éditeur de Code inclura des éléments du schéma XSD dans la liste IntelliSense des variables de membre valide pour <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="87f50-104">If you include an XML Schema Definition (XSD) file in your project and import the target namespace of the schema by using the `Imports` statement, the Code Editor will include elements from the XSD schema in the IntelliSense list of valid member variables for <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="87f50-105">L’illustration suivante montre la liste de membres IntelliSense pour un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="87f50-105">The following illustration shows the IntelliSense members list for an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="87f50-106">![XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span><span class="sxs-lookup"><span data-stu-id="87f50-106">![XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span></span>  
<span data-ttu-id="87f50-107">XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="87f50-107">XML IntelliSense</span></span>  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a><span data-ttu-id="87f50-108">Activer XML IntelliSense dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87f50-108">Enabling XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="87f50-109">Pour activer XML IntelliSense dans Visual Basic, vous devez inclure un fichier de schéma XSD dans votre projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87f50-109">To enable XML IntelliSense in Visual Basic, you must include an XSD schema file in your Visual Basic project.</span></span> <span data-ttu-id="87f50-110">Vous devez également importer l’espace de noms cible du schéma XSD dans votre fichier de code à l’aide de la `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="87f50-110">You must also import the target namespace for the XSD schema into your code file by using the `Imports` statement.</span></span> <span data-ttu-id="87f50-111">Vous pouvez également ajouter l’espace de noms cible à la liste de l’espace de noms au niveau du projet à l’aide de la **références** page du Concepteur de projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87f50-111">Alternatively, you can add the target namespace to the project-level namespace list by using the **References** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="87f50-112">Pour obtenir des exemples, consultez [Comment : activer XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span><span class="sxs-lookup"><span data-stu-id="87f50-112">For examples, see [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span> <span data-ttu-id="87f50-113">Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) et [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="87f50-113">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) and [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="87f50-114">Notez que par défaut, vous ne pouvez pas voir les fichiers de schéma XSD dans les projets Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87f50-114">Note that by default you cannot see XSD schema files in Visual Basic projects.</span></span> <span data-ttu-id="87f50-115">Il se peut que vous deviez cliquer sur le **afficher tous les fichiers** pour sélectionner un fichier XSD à inclure dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="87f50-115">You may have to click the **Show All Files** button to select an XSD file to include in your project.</span></span>  
  
### <a name="generating-a-schema-file-schema-inference"></a><span data-ttu-id="87f50-116">Génération d’un fichier de schéma (inférence de schéma)</span><span class="sxs-lookup"><span data-stu-id="87f50-116">Generating a Schema File (Schema Inference)</span></span>  
 <span data-ttu-id="87f50-117">Vous pouvez créer un schéma XSD pour un fichier XML existant en déduisant le schéma XSD à l’aide des outils XML Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87f50-117">You can create an XSD schema for an existing XML file by inferring the XSD schema by using Visual Studio XML tools.</span></span>  
  
-   <span data-ttu-id="87f50-118">À compter de SP1, vous pouvez utiliser l’Assistant schéma XML vers pour créer un jeu de schémas XML qui est déduit à partir d’un ou plusieurs documents XML et l’inclure dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="87f50-118">Starting in SP1, you can use the XML to Schema Wizard to create an XML Schema set that is inferred from one or more XML documents and include it your project.</span></span> <span data-ttu-id="87f50-119">Vous pouvez utiliser n’importe quelle combinaison de documents XML sous la forme de fichiers texte, XML à partir d’une adresse HTTP Internet ou code XML tapé ou collé dans l’Assistant schéma XML vers.</span><span class="sxs-lookup"><span data-stu-id="87f50-119">You can use any combination of XML documents in the form of text files, XML from HTTP Internet addresses, or XML that is typed or pasted into the XML to Schema Wizard.</span></span> <span data-ttu-id="87f50-120">Pour accéder à l’Assistant schéma XML vers, cliquez sur **ajouter un nouvel élément** sur la **projet** menu et ajoutez un **XML au schéma** modèle à partir de le le **données** ou **éléments communs** groupe de modèles.</span><span class="sxs-lookup"><span data-stu-id="87f50-120">To access the XML to Schema Wizard, click **Add New Item** on the **Project** menu and add an **XML to Schema** template from either the **Data** or **Common Items** template group.</span></span> <span data-ttu-id="87f50-121">Une fois que vous avez inclus toutes les sources de document XML pour déduire le jeu de schémas XML à partir de, cliquez sur **OK** pour créer le schéma déduit jeu.</span><span class="sxs-lookup"><span data-stu-id="87f50-121">After you have included all the XML document sources to infer the XML Schema set from, click **OK** to create the inferred schema set.</span></span> <span data-ttu-id="87f50-122">Pour plus d’informations, consultez [Assistant XML vers schéma](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="87f50-122">For more information, see [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).</span></span>  
  
-   <span data-ttu-id="87f50-123">Vous pouvez également utiliser l’éditeur XML de Visual Studio pour déduire un schéma XSD à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="87f50-123">You can also use the Visual Studio XML Editor to infer an XSD schema set from an XML file.</span></span> <span data-ttu-id="87f50-124">Pour créer un schéma XML défini à l’aide de l’éditeur XML, ouvrez un fichier XML dans le Concepteur XML de Visual Studio, puis cliquez **Create Schema** sur la **XML** menu.</span><span class="sxs-lookup"><span data-stu-id="87f50-124">To create an XML schema set by using the XML Editor, open an XML file in the Visual Studio XML Designer and then click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="87f50-125">Après avoir créé le jeu de schémas XSD, vous pouvez enregistrer le jeu de schémas créés dans un ou plusieurs fichiers XSD et les inclure dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="87f50-125">After you create the XSD schema set, you can save the created schema set to one or more XSD files and include them in your project.</span></span> <span data-ttu-id="87f50-126">Pour plus d’informations, consultez[Comment : activer XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span><span class="sxs-lookup"><span data-stu-id="87f50-126">For more information, see[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span>  
  
 <span data-ttu-id="87f50-127">Notez que les différents jeux de schémas XSD peut-être être déduits à partir de plusieurs documents XML conçus pour avoir le même schéma.</span><span class="sxs-lookup"><span data-stu-id="87f50-127">Note that different XSD schema sets might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="87f50-128">Cela peut se produire lorsque des éléments et attributs particuliers sont trouvées dans un fichier XML et pas dans un autre, ou lorsque les éléments sont inclus dans un ordre différent, par exemple.</span><span class="sxs-lookup"><span data-stu-id="87f50-128">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="87f50-129">Vous devez examiner les jeux de schémas XSD déduits pour l’exhaustivité et la précision lorsque vous utilisez l’inférence de schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="87f50-129">You should review inferred XSD schema sets for completeness and accuracy when you use XSD schema inference.</span></span>  
  
## <a name="member-list"></a><span data-ttu-id="87f50-130">Liste des membres</span><span class="sxs-lookup"><span data-stu-id="87f50-130">Member List</span></span>  
 <span data-ttu-id="87f50-131">Après avoir tapé un point (.) pour délimiter une instance d’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objet (ou une instance de `IEnumerable(Of XElement)` ou `IEnumerable(Of XDocument)`), Visual Basic IntelliSense affiche une liste des membres d’objet possibles.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="87f50-131">After you type a period (.) to delimit an instance of an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object (or an instance of `IEnumerable(Of XElement)` or `IEnumerable(Of XDocument)`), Visual Basic IntelliSense displays a list of possible object members.</span></span> <span data-ttu-id="87f50-132">La liste initiale inclut trois options qui représentent les propriétés d’axe XML, comme décrit dans la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="87f50-132">The initial list includes three options that represent XML axis properties, as described in the following list.</span></span>  
  
|<span data-ttu-id="87f50-133">Option</span><span class="sxs-lookup"><span data-stu-id="87f50-133">Option</span></span>|<span data-ttu-id="87f50-134">Description</span><span class="sxs-lookup"><span data-stu-id="87f50-134">Description</span></span>|  
|---|---|  
|**\< >**|<span data-ttu-id="87f50-135">Sélectionnez cette option pour afficher des éléments d’une liste d’enfants possibles.</span><span class="sxs-lookup"><span data-stu-id="87f50-135">Select this option to show a list of possible child elements.</span></span> <span data-ttu-id="87f50-136">Pour plus d’informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et <xref:System.Xml.Linq.XContainer.Elements%2A>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="87f50-136">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
|**@**|<span data-ttu-id="87f50-137">Sélectionnez cette option pour afficher une liste d’attributs possibles.</span><span class="sxs-lookup"><span data-stu-id="87f50-137">Select this option to show a list of possible attributes.</span></span> <span data-ttu-id="87f50-138">Pour plus d’informations, consultez [propriétés d’axe XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md). Cette option est disponible uniquement pour les objets de type <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="87f50-138">For more information, see [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).This option is available only for objects of type <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="87f50-139">**…\< >**</span><span class="sxs-lookup"><span data-stu-id="87f50-139">**…\< >**</span></span>|<span data-ttu-id="87f50-140">Sélectionnez cette option pour afficher une liste d’éléments descendants.</span><span class="sxs-lookup"><span data-stu-id="87f50-140">Select this option to show a list of possible descendant elements.</span></span> <span data-ttu-id="87f50-141">Pour plus d’informations, consultez [Comment : accéder aux éléments de Descendant XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) et <xref:System.Xml.Linq.XContainer.Elements%2A>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="87f50-141">For more information, see [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
  
 <span data-ttu-id="87f50-142">Sélectionnez ou commencez à taper une des options de la liste XML.</span><span class="sxs-lookup"><span data-stu-id="87f50-142">Select or begin typing any of the XML options from the list.</span></span> <span data-ttu-id="87f50-143">La liste des membres affichera ensuite les membres potentiels du schéma XML qui sont spécifiques à l’option sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="87f50-143">The member list will then display potential members from the XML schema that are specific to the selected option.</span></span> <span data-ttu-id="87f50-144">Si vous avez des espaces de noms XML importés associés à un préfixe d’espace de noms XML spécifique, une liste de préfixes d’espace de noms XML potentiels est incluse dans la liste des membres.</span><span class="sxs-lookup"><span data-stu-id="87f50-144">If you have XML namespaces imported that are associated with a specific XML namespace prefix, a list of potential XML namespace prefixes is included in the member list.</span></span>  
  
 <span data-ttu-id="87f50-145">Par exemple, considérez le schéma XSD suivant.</span><span class="sxs-lookup"><span data-stu-id="87f50-145">For example, consider the following XSD schema.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"   
           elementFormDefault="qualified"   
           targetNamespace="http://SamplePurchaseOrder"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="PurchaseOrders">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="PurchaseOrder">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Address" />  
              <xs:element name="Items" />  
              <xs:element name="Comment" />  
            </xs:sequence>  
            <xs:attribute name="PurchaseOrderNumber" type="xs:unsignedShort" use="required" />  
            <xs:attribute name="OrderDate" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="87f50-146">XML Valid pour le schéma XSD se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="87f50-146">Valid XML for the XSD schema would resemble the following.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 <span data-ttu-id="87f50-147">Si vous incluez ce fichier de schéma XSD dans un projet et importez l’espace de noms cible du schéma XSD dans votre fichier de code ou un projet, Visual Basic IntelliSense affiche les membres à partir du schéma lorsque vous tapez votre code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87f50-147">If you include this XSD schema file in a project and import the target namespace from the XSD schema into your code file or project, Visual Basic IntelliSense displays members from the schema as you type your Visual Basic code.</span></span> <span data-ttu-id="87f50-148">Si l’espace de noms cible pour le schéma XSD est importé comme espace de noms par défaut et que vous tapez la commande suivante, IntelliSense affiche une liste d’éléments enfants possibles pour le `PurchaseOrder` (élément XML).</span><span class="sxs-lookup"><span data-stu-id="87f50-148">If the target namespace for the XSD schema is imported as the default namespace and you type the following, IntelliSense displays a list of possible child elements for the `PurchaseOrder` XML element.</span></span>  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 <span data-ttu-id="87f50-149">La liste se compose des éléments adresse, commentaire et éléments.</span><span class="sxs-lookup"><span data-stu-id="87f50-149">The list consists of the Address, Comment, and Items elements.</span></span>  
  
### <a name="certainty-levels-for-intellisense-list-items"></a><span data-ttu-id="87f50-150">Niveaux de certitude pour les éléments de liste IntelliSense</span><span class="sxs-lookup"><span data-stu-id="87f50-150">Certainty Levels for IntelliSense List Items</span></span>  
 <span data-ttu-id="87f50-151">Détermination du type XSD à utiliser pour IntelliSense n’est pas exact.</span><span class="sxs-lookup"><span data-stu-id="87f50-151">Determining the XSD type to use for IntelliSense is not exact.</span></span> <span data-ttu-id="87f50-152">En conséquence, XML IntelliSense affichera souvent une liste développée de membres possibles.</span><span class="sxs-lookup"><span data-stu-id="87f50-152">As a result, XML IntelliSense will often show an expanded list of possible members.</span></span> <span data-ttu-id="87f50-153">Pour sélectionner un élément dans la liste des membres IntelliSense, les éléments sont affichés avec une indication du niveau de certitude que XML IntelliSense propose pour un membre particulier.</span><span class="sxs-lookup"><span data-stu-id="87f50-153">To aid you in selecting an item from the IntelliSense member list, items are displayed with an indication of the level of certainty that XML IntelliSense has for a particular member.</span></span>  
  
 <span data-ttu-id="87f50-154">Quelquefois XML IntelliSense peut identifier un type spécifique à partir du schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="87f50-154">Sometimes XML IntelliSense can identify a specific type from the XSD schema.</span></span> <span data-ttu-id="87f50-155">Dans ces cas, il affichera des éléments enfants possibles, des attributs ou des éléments descendants pour ce type XSD avec un degré élevé de certitude.</span><span class="sxs-lookup"><span data-stu-id="87f50-155">In these cases, it will display possible child elements, attributes, or descendant elements for that XSD type with a high degree of certainty.</span></span> <span data-ttu-id="87f50-156">Ces éléments sont identifiés par une coche.</span><span class="sxs-lookup"><span data-stu-id="87f50-156">These items are identified with a check mark.</span></span>  
  
 <span data-ttu-id="87f50-157">Cependant, parfois XML IntelliSense n’est pas en mesure d’identifier un type spécifique à partir du schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="87f50-157">However, sometimes XML IntelliSense is not able to identify a specific type from the XSD schema.</span></span> <span data-ttu-id="87f50-158">Dans ces cas, il affichera une liste développée des éléments enfants possibles, des attributs ou des éléments descendants à partir du schéma XSD pour le projet avec un faible degré de certitude.</span><span class="sxs-lookup"><span data-stu-id="87f50-158">In these cases, it will display an expanded list of possible child elements, attributes, or descendant elements from the XSD schema for the project with a low degree of certainty.</span></span> <span data-ttu-id="87f50-159">Ces éléments sont identifiés par un point d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="87f50-159">These items are identified with a question mark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f50-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87f50-160">See Also</span></span>  
 <span data-ttu-id="87f50-161">[Comment : activer XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span><span class="sxs-lookup"><span data-stu-id="87f50-161">[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span></span>  
<span data-ttu-id="87f50-162"> [Assistant schéma XML vers](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="87f50-162"> [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span></span>  
<span data-ttu-id="87f50-163"> [Imports, instruction (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="87f50-163"> [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="87f50-164"> [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="87f50-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="87f50-165"> [Propriété d’axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="87f50-165"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="87f50-166"> [Propriété d’axe Descendant XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="87f50-166"> [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span></span>  
<span data-ttu-id="87f50-167"> [Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="87f50-167"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>

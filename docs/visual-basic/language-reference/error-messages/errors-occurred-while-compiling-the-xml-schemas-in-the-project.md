---
title: "Des erreurs se sont produites lors de la compilation des schémas Xml du projet"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords: BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="b23b5-102">Des erreurs se sont produites lors de la compilation des schémas Xml du projet</span><span class="sxs-lookup"><span data-stu-id="b23b5-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="b23b5-103">Erreurs se sont produites lors de la compilation des schémas XML dans le projet.</span><span class="sxs-lookup"><span data-stu-id="b23b5-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="b23b5-104">Pour cette raison, XML IntelliSense n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="b23b5-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="b23b5-105">Il existe une erreur dans un schéma de définition de schéma XML (XSD) inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="b23b5-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="b23b5-106">Cette erreur se produit lorsque vous ajoutez un fichier de schéma (.xsd) XSD qui est en conflit avec le schéma XSD existant défini pour le projet.</span><span class="sxs-lookup"><span data-stu-id="b23b5-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="b23b5-107">**ID d’erreur :** BC36810</span><span class="sxs-lookup"><span data-stu-id="b23b5-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b23b5-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b23b5-108">To correct this error</span></span>  
  
-   <span data-ttu-id="b23b5-109">Double-cliquez sur l’avertissement dans la **liste d’erreurs** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b23b5-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="b23b5-110">Visual Basic vous dirige vers l’emplacement dans le fichier XSD qui est la source de l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="b23b5-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="b23b5-111">Corrigez l’erreur dans le schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="b23b5-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="b23b5-112">Assurez-vous que tous les requises des fichiers XSD schéma (.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="b23b5-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="b23b5-113">Vous devrez peut-être cliquer sur **afficher tous les fichiers** sur la **projet** menu pour afficher votre .xsd dans les fichiers **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="b23b5-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="b23b5-114">Cliquez sur un fichier .xsd, puis sur **inclure dans le projet** pour inclure le fichier dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="b23b5-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="b23b5-115">Si vous utilisez l’Assistant schéma XML vers, cette erreur peut se produire si vous déduisez des schémas à plusieurs fois à partir de la même source.</span><span class="sxs-lookup"><span data-stu-id="b23b5-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="b23b5-116">Dans ce cas, vous pouvez supprimer les fichiers de schéma XSD existants à partir du projet, y ajouter un nouveau code XML pour le modèle d’élément de schéma, puis fournir le code XML à l’Assistant schéma de toutes les sources XML applicables pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="b23b5-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="b23b5-117">Si aucune erreur n’est identifiée dans votre schéma XSD, le compilateur XML peut-être pas suffisamment d’informations pour fournir un message d’erreur détaillé.</span><span class="sxs-lookup"><span data-stu-id="b23b5-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="b23b5-118">Vous serez peut-être en mesure d’obtenir davantage d’informations sur l’erreur si vous vérifiez que les espaces de noms XML pour les fichiers .xsd inclus dans votre projet correspondent aux espaces de noms XML identifié pour le schéma XML défini dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b23b5-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b23b5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b23b5-119">See Also</span></span>  
 [<span data-ttu-id="b23b5-120">Liste d’erreurs, fenêtre</span><span class="sxs-lookup"><span data-stu-id="b23b5-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)  
 [<span data-ttu-id="b23b5-121">XML</span><span class="sxs-lookup"><span data-stu-id="b23b5-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)

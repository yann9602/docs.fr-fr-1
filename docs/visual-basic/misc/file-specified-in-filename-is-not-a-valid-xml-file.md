---
title: "Le fichier spécifié dans FileName n’est pas un fichier XML valide"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3275608a1871ac981eb5b3aa39f0be6ab4e758e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="609f7-102">Le fichier spécifié dans FileName n’est pas un fichier XML valide</span><span class="sxs-lookup"><span data-stu-id="609f7-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="609f7-103">Le nom de fichier fourni n’est pas un fichier XML valide.</span><span class="sxs-lookup"><span data-stu-id="609f7-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="609f7-104">Pour spécifier la structure et le contenu autorisés d’un document XML, vous pouvez utiliser une définition de type de document (DTD), un schéma Microsoft XML-Data Reduced (XDR) ou un schéma de langage de définition de schéma XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="609f7-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="609f7-105">Les schémas XSD constituent la meilleure façon de spécifier des grammaires XML dans le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="609f7-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="609f7-106">Dans certaines versions antérieures de Visual Studio, le **Concepteur XML** est le concepteur pour le schéma XML et les datasets typés.</span><span class="sxs-lookup"><span data-stu-id="609f7-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="609f7-107">Vous pouvez toujours utiliser le **Concepteur XML** pour créer et modifier des fichiers de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="609f7-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="609f7-108">Toutefois, dans [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], c’est le **Concepteur de Dataset**qui permet de créer et de modifier des datasets typés.</span><span class="sxs-lookup"><span data-stu-id="609f7-108">However, in [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="609f7-109">Pour plus d’informations, consultez [création et modification de données typés](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="609f7-109">For more information, see [Creating and Editing Typed Datasets](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="609f7-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="609f7-110">To correct this error</span></span>  
  
-   <span data-ttu-id="609f7-111">Vérifiez que le nom du fichier que vous fournissez est correct.</span><span class="sxs-lookup"><span data-stu-id="609f7-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="609f7-112">Vérifiez que le fichier spécifié contient le code XML valide. Pour cela, chargez le fichier XML à vérifier dans le **Concepteur XML**.</span><span class="sxs-lookup"><span data-stu-id="609f7-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="609f7-113">Dans le menu **XML** , cliquez sur **Valider le XML**.</span><span class="sxs-lookup"><span data-stu-id="609f7-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="609f7-114">Les erreurs sont répertoriées dans la **Liste des tâches**.</span><span class="sxs-lookup"><span data-stu-id="609f7-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="609f7-115">Si le fichier XML comprend un schéma XML associé, vérifiez que les éléments apparaissent dans la structure définie et que le contenu de chaque élément est conforme aux types de données déclarés qui sont spécifiés dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="609f7-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609f7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="609f7-116">See Also</span></span>  
 <xref:System.Xml>  
 [<span data-ttu-id="609f7-117">Guide pratique pour analyser des chemins</span><span class="sxs-lookup"><span data-stu-id="609f7-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

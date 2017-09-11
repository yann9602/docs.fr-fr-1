---
title: "Fichier spécifié dans le nom de fichier n’est pas un fichier XML valide | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8b46b9d896f0dce401992e8a20e040b85091ba5d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="1bca3-102">Le fichier spécifié dans FileName n’est pas un fichier XML valide</span><span class="sxs-lookup"><span data-stu-id="1bca3-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="1bca3-103">Le nom de fichier fourni n’est pas un fichier XML valide.</span><span class="sxs-lookup"><span data-stu-id="1bca3-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="1bca3-104">Pour spécifier la structure et le contenu autorisés d’un document XML, vous pouvez utiliser une définition de type de document (DTD), un schéma Microsoft XML-Data Reduced (XDR) ou un schéma de langage de définition de schéma XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="1bca3-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="1bca3-105">Schémas XSD représentent la méthode préférée pour spécifier des grammaires XML dans le [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="1bca3-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bca3-106">Dans certaines versions antérieures de Visual Studio, le **Concepteur XML** est le concepteur pour le schéma XML et les datasets typés.</span><span class="sxs-lookup"><span data-stu-id="1bca3-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="1bca3-107">Vous pouvez toujours utiliser le **Concepteur XML** pour créer et modifier des fichiers de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="1bca3-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="1bca3-108">Toutefois, dans [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)], le concepteur pour créer et modifier des groupes de données typés est la **Concepteur de Dataset**.</span><span class="sxs-lookup"><span data-stu-id="1bca3-108">However, in [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="1bca3-109">Pour plus d’informations, consultez [création et modification de données typés](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="1bca3-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bca3-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1bca3-110">To correct this error</span></span>  
  
-   <span data-ttu-id="1bca3-111">Vérifiez que le nom du fichier que vous fournissez est correct.</span><span class="sxs-lookup"><span data-stu-id="1bca3-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="1bca3-112">Vérifiez que le fichier spécifié contient le code XML valide. Pour cela, chargez le fichier XML à vérifier dans le **Concepteur XML**.</span><span class="sxs-lookup"><span data-stu-id="1bca3-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="1bca3-113">Dans le menu **XML** , cliquez sur **Valider le XML**.</span><span class="sxs-lookup"><span data-stu-id="1bca3-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="1bca3-114">Les erreurs sont répertoriées dans la **Liste des tâches**.</span><span class="sxs-lookup"><span data-stu-id="1bca3-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="1bca3-115">Si le fichier XML comprend un schéma XML associé, vérifiez que les éléments apparaissent dans la structure définie et que le contenu de chaque élément est conforme aux types de données déclarés qui sont spécifiés dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="1bca3-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bca3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bca3-116">See Also</span></span>  
 <span data-ttu-id="1bca3-117"><xref:System.Xml></xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="1bca3-117"><xref:System.Xml></span></span>   
<span data-ttu-id="1bca3-118"> [Guide pratique : analyser des chemins d’accès](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span><span class="sxs-lookup"><span data-stu-id="1bca3-118"> [How to: Parse File Paths](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span></span>

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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2fa595ab411fdd300327db9e1fcca1e3156c7eed
ms.lasthandoff: 03/13/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Le fichier spécifié dans FileName n’est pas un fichier XML valide
Le nom de fichier fourni n’est pas un fichier XML valide. Pour spécifier la structure et le contenu autorisés d’un document XML, vous pouvez utiliser une définition de type de document (DTD), un schéma Microsoft XML-Data Reduced (XDR) ou un schéma de langage de définition de schéma XML (XSD). Schémas XSD représentent la méthode préférée pour spécifier des grammaires XML dans le [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  Dans certaines versions antérieures de Visual Studio, le **Concepteur XML** est le concepteur pour le schéma XML et les datasets typés. Vous pouvez toujours utiliser le **Concepteur XML** pour créer et modifier des fichiers de schéma XML. Toutefois, dans [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)], le concepteur pour créer et modifier des groupes de données typés est la **Concepteur de Dataset**. Pour plus d’informations, consultez [création et modification de données typés](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que le nom du fichier que vous fournissez est correct.  
  
-   Vérifiez que le fichier spécifié contient le code XML valide. Pour cela, chargez le fichier XML à vérifier dans le **Concepteur XML**. Dans le menu **XML** , cliquez sur **Valider le XML**. Les erreurs sont répertoriées dans la **Liste des tâches**.  
  
-   Si le fichier XML comprend un schéma XML associé, vérifiez que les éléments apparaissent dans la structure définie et que le contenu de chaque élément est conforme aux types de données déclarés qui sont spécifiés dans le schéma.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml></xref:System.Xml>   
 [Guide pratique : analyser des chemins d’accès](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

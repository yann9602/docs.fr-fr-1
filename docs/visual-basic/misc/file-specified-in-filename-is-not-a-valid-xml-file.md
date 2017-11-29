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
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Le fichier spécifié dans FileName n’est pas un fichier XML valide
Le nom de fichier fourni n’est pas un fichier XML valide. Pour spécifier la structure et le contenu autorisés d’un document XML, vous pouvez utiliser une définition de type de document (DTD), un schéma Microsoft XML-Data Reduced (XDR) ou un schéma de langage de définition de schéma XML (XSD). Les schémas XSD constituent la meilleure façon de spécifier des grammaires XML dans le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  Dans certaines versions antérieures de Visual Studio, le **Concepteur XML** est le concepteur pour le schéma XML et les datasets typés. Vous pouvez toujours utiliser le **Concepteur XML** pour créer et modifier des fichiers de schéma XML. Toutefois, dans [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], c’est le **Concepteur de Dataset**qui permet de créer et de modifier des datasets typés. Pour plus d’informations, consultez [création et modification de données typés](/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que le nom du fichier que vous fournissez est correct.  
  
-   Vérifiez que le fichier spécifié contient le code XML valide. Pour cela, chargez le fichier XML à vérifier dans le **Concepteur XML**. Dans le menu **XML** , cliquez sur **Valider le XML**. Les erreurs sont répertoriées dans la **Liste des tâches**.  
  
-   Si le fichier XML comprend un schéma XML associé, vérifiez que les éléments apparaissent dans la structure définie et que le contenu de chaque élément est conforme aux types de données déclarés qui sont spécifiés dans le schéma.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml>  
 [Guide pratique pour analyser des chemins](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

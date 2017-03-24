---
title: /linkresource (Visual Basic) | Documents Microsoft
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: fafde6563340189108a879b82e7e880aca690b39
ms.lasthandoff: 03/13/2017

---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
Crée un lien à une ressource managée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Obligatoire. Le fichier de ressources à lier à l’assembly. Si le nom de fichier contient un espace, placez le nom entre guillemets (« »).  
  
 `identifier`  
 Facultatif. Nom logique de la ressource. Le nom qui est utilisé pour charger la ressource. La valeur par défaut est le nom du fichier. Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste d’assembly, par exemple : `/linkres:filename.res,myname.res,public`. Par défaut, `filename` est public dans l’assembly.  
  
## <a name="remarks"></a>Remarques  
 Le `/linkresource` option n’incorpore pas le fichier de ressources dans le fichier de sortie ; Utilisez la `/resource` option pour ce faire.  
  
 Le `/linkresource` option requiert l’une de le `/target` options autres que `/target:module`.  
  
 Si `filename` est un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] le fichier de ressources créé, par exemple, par le [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l’environnement de développement, il est accessible à l’aide des membres de la <xref:System.Resources>espace de noms.</xref:System.Resources> (Pour plus d’informations, consultez <xref:System.Resources.ResourceManager>.)</xref:System.Resources.ResourceManager> Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la <xref:System.Reflection.Assembly>classe.</xref:System.Reflection.Assembly>  
  
 Le nom de fichier peut être n’importe quel format de fichier. Par exemple, vous souhaiterez une DLL native de l’assembly, de sorte que peut être installé dans le global assembly cache et accessible à partir du code managé dans l’assembly.  
  
 La forme abrégée de `/linkresource` est `/linkres`.  
  
> [!NOTE]
>  La `/linkresource` option n’est pas disponible à partir de l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et des liens vers le fichier de ressources `Rf.resource`.  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

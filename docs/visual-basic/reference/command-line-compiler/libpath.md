---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2be2c460fddf2e8ea4fe1239ec073f208c072d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="libpath"></a>/libpath
Spécifie l’emplacement des assemblys référencés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`dirList`|Obligatoire. Délimitée par des points-virgules de liste de répertoires pour le compilateur doit vérifier si un assembly référencé est introuvable dans le répertoire de travail actif (le répertoire à partir duquel vous appelez le compilateur) ou le répertoire du système du common language runtime. Si le nom de répertoire contient un espace, placez-le entre guillemets (« »).|  
  
## <a name="remarks"></a>Remarques  
 Le `/libpath` option spécifie l’emplacement des assemblys référencés par le [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.  
  
 Le compilateur recherche les références d’assembly qui ne sont pas complètes dans l’ordre suivant :  
  
1.  Répertoire de travail actuel. Il s’agit du répertoire à partir duquel le compilateur est appelé.  
  
2.  Répertoire système du common language runtime.  
  
3.  Répertoires spécifiés par `/libpath`.  
  
4.  Répertoires spécifiés par la variable d’environnement LIB.  
  
 Le `/libpath` option est additif ; en spécifiant plus qu’une seule fois ajoute aux valeurs précédentes.  
  
 Utilisez `/reference` pour spécifier une référence d’assembly.  
  
|Pour définir /libpath dans Visual Studio environnement de développement intégré|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Références**.<br />3.  Cliquez sur le **référencer les chemins d’accès...**  bouton.<br />4.  Dans le **chemins d’accès de référence** boîte de dialogue, entrez le nom du répertoire dans le **dossier :** boîte.<br />5.  Cliquez sur **ajouter un dossier**.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` pour créer un fichier .exe. Le compilateur recherche dans le répertoire de travail, dans le répertoire racine du lecteur C: et dans le répertoire de nouveaux assemblys du lecteur C:, références d’assembly.  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

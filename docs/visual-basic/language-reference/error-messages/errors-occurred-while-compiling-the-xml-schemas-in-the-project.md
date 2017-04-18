---
title: "Erreurs se sont produites lors de la compilation des schémas XML dans le projet | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
dev_langs:
- VB
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cf04e85da98db53d1c78269169571936f708cd21
ms.lasthandoff: 03/13/2017

---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Des erreurs se sont produites lors de la compilation des schémas Xml du projet
Erreurs lors de la compilation des schémas XML dans le projet. Pour cette raison, XML IntelliSense n’est pas disponible.  
  
 Il existe une erreur dans un schéma de définition de schéma XML (XSD) inclus dans le projet. Cette erreur se produit lorsque vous ajoutez un fichier de schéma (.xsd) XSD qui est en conflit avec le schéma XSD existant défini pour le projet.  
  
 **ID d’erreur :** BC36810  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Double-cliquez sur l’avertissement dans la **liste d’erreurs** fenêtre. Visual Basic vous dirigera vers l’emplacement dans le fichier XSD qui est la source de l’avertissement. Corrigez l’erreur dans le schéma XSD.  
  
-   Assurez-vous que tous les fichiers de schéma (.xsd) XSD sont inclus dans le projet. Vous devrez peut-être cliquer sur **afficher tous les fichiers** sur la **projet** menu pour afficher votre .xsd dans des fichiers **l’Explorateur de solutions**. Cliquez sur un fichier .xsd, puis cliquez sur **inclure dans le projet** pour inclure le fichier dans votre projet.  
  
-   Si vous utilisez l’Assistant schéma XML vers, cette erreur peut se produire si vous déduisez des schémas à plusieurs fois à partir de la même source. Dans ce cas, vous pouvez supprimer les fichiers de schéma XSD existants du projet, ajoutez un nouveau fichier XML de modèle d’élément de schéma et fournissez le code XML à l’Assistant schéma avec toutes les sources XML applicables pour votre projet.  
  
-   Si aucune erreur n’est identifiée dans votre schéma XSD, le compilateur XML peut-être pas suffisamment d’informations pour fournir un message d’erreur détaillé. Vous pourrez obtenir davantage d’informations sur l’erreur si vous vous assurez que les espaces de noms XML pour les fichiers .xsd inclus dans votre projet correspondent aux espaces de noms XML identifiés pour le schéma XML défini dans Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre liste d’erreurs](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window)   
 [XML IntelliSense dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)

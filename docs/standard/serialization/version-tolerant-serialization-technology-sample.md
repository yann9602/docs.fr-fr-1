---
title: "Sérialisation avec tolérance de version, exemple de technologie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 43057a4b0014ac2ea8aec6f298ccc0b2d9103154
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="version-tolerant-serialization-technology-sample"></a>Sérialisation avec tolérance de version, exemple de technologie
[Télécharger l’exemple](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Cet exemple illustre les fonctionnalités de tolérance de version de la sérialisation .NET. L'exemple génère des applications qui utilisent différentes versions de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour sérialiser et désérialiser des données. En dépit de la présence de versions de type différent, les applications communiquent de façon transparente. Pour plus d’informations, consultez [Sérialisation avec tolérance de version](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Pour générer l'exemple à partir de l'invite de commandes :  
  
1.  Ouvrez une fenêtre d'invite de commandes et accédez à l'un des sous-répertoires spécifiques au langage (sous l'application V1 ou l'application V2) pour l'exemple.  
  
2.  Tapez **msbuild.exe \<ver> application.sln** sur la ligne de commande (où \<ver> est v1 ou v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Pour générer l'exemple à l'aide de Visual Studio  
  
1.  Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez à l'un des sous-répertoires spécifiques aux différents langages de l'exemple.  
  
2.  Accédez au sous-répertoire de l'application V1 du répertoire sélectionné à l'étape précédente.  
  
3.  Double-cliquez sur l'icône de V1 Application.sln pour ouvrir le fichier dans Visual Studio.  
  
4.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
5.  Accédez au sous-répertoire de l'application V2 et répétez les deux étapes précédentes pour générer l'application V2.  
  
 Les applications seront générées dans le sous-répertoire \bin ou \bin\Debug par défaut de leur projet respectif.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Dans la fenêtre d'invite de commandes, accédez au sous-répertoire spécifique au langage que vous avez sélectionné lors de la création des exemples d'applications.  
  
2.  Tapez **runme.cmd** sur la ligne de commande pour exécuter en même temps les deux applications.  
  
 Vous pouvez aussi accéder aux répertoires qui contiennent les nouveaux fichiers exécutables et les exécuter séquentiellement.  
  
> [!NOTE]
>  L'exemple génère des applications console. Vous devez les lancer et les exécuter dans une fenêtre d'invite de commandes pour consulter leur sortie.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>   
 <xref:System.IO.FileStream>


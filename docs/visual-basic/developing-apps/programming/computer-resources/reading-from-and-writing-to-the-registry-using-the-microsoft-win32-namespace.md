---
title: "Lecture et &#233;criture dans le Registre &#224; l&#39;aide de l&#39;espace de noms Microsoft.Win32 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registre, Visual Basic"
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Lecture et &#233;criture dans le Registre &#224; l&#39;aide de l&#39;espace de noms Microsoft.Win32 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Même si `My.Computer.Registry` doit normalement couvrir vos principaux besoins quand vous programmez le Registre, vous pouvez également utiliser les classes <xref:Microsoft.Win32.Registry> et <xref:Microsoft.Win32.RegistryKey> dans l’espace de noms <xref:Microsoft.Win32> du [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Clés dans la classe de Registre  
 La classe <xref:Microsoft.Win32.Registry> fournit les clés de Registre de base qui peuvent être utilisées pour accéder aux sous-clés et à leurs valeurs. Les clés de base proprement dites sont en lecture seule. Le tableau suivant répertorie et décrit les sept clés exposées par la classe <xref:Microsoft.Win32.Registry>.  
  
|**Clé**|**Description**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Définit les types de documents et les propriétés associées à ces types.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Contient des informations sur la configuration matérielle qui ne sont pas propres à l’utilisateur.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Contient des informations sur les préférences de l’utilisateur actuel, telles que les variables d’environnement.|  
|<xref:Microsoft.Win32.Registry.DynData>|Contient des données de Registre dynamiques, telles que celles utilisées par les pilotes de périphériques virtuels.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Contient cinq sous-clés (Hardware, SAM, Security, Software et System) qui contiennent les données de configuration de l’ordinateur local.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Contient des informations sur les performances des composants logiciels.|  
|<xref:Microsoft.Win32.Registry.Users>|Contient des informations sur les préférences de l’utilisateur par défaut.|  
  
> [!IMPORTANT]
>  Il est plus sûr d’écrire des données sur l’utilisateur actuel (<xref:Microsoft.Win32.Registry.CurrentUser>) que sur l’ordinateur local (<xref:Microsoft.Win32.Registry.LocalMachine>). Une condition généralement appelée « usurpation » se produit quand la clé que vous créez a été créée précédemment par un autre processus, potentiellement malveillant. Pour éviter ce problème, utilisez une méthode, comme <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, qui retourne `Nothing` si la clé n’existe pas encore.  
  
## <a name="reading-a-value-from-the-registry"></a>Lecture d’une valeur à partir du Registre  
 Le code suivant montre comment lire une chaîne à partir de HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/reading-from-and-writing_1.vb)]  
  
 Le code suivant lit, incrémente puis écrit une chaîne dans HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/reading-from-and-writing_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.SystemException>   
 <xref:System.ApplicationException>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Try...Catch...Finally (instruction)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Lecture et écriture dans le Registre](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [Sécurité et Registre](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
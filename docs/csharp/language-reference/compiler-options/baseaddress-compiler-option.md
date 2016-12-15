---
title: "/baseaddress (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/dllbase"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "baseaddress compiler option [C#]"
  - "/baseaddress compiler option [C#]"
  - "-baseaddress compiler option [C#]"
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /baseaddress (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/baseaddress** vous permet de spécifier l'adresse de base préférée à laquelle doit être chargée une DLL.  Pour plus d'informations sur le moment et pourquoi utiliser cette option, consultez [Améliorer le temps de démarrage de l'application](http://go.microsoft.com/fwlink/?LinkId=107043) et [Journal Web Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## Syntaxe  
  
```  
/baseaddress:address  
```  
  
## Arguments  
 `address`  
 Adresse de base de la DLL.  Cette adresse peut être spécifiée sous forme d'un nombre décimal, hexadécimal ou octal.  
  
## Notes  
 L'adresse de base par défaut pour une DLL est déterminée par le Common Language Runtime du .NET Framework.  
  
 Sachez que le dernier chiffre de cette adresse sera arrondi.  Par exemple, si vous spécifiez l'adresse 0x11110001, elle est arrondie à 0x11110000.  
  
 Utilisez SN.EXE avec l'option \-R pour terminer le processus de signature d'une DLL.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancé**.  
  
4.  Modifiez la propriété **Adresse de base de la DLL**.  
  
     Pour définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>  
  
## Voir aussi  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
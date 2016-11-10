---
title: "Bibliothèques de framework"
description: "Bibliothèques de framework"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
translationtype: Human Translation
ms.sourcegitcommit: 093b852fe1ed2307ebce914381fe47388b435c95
ms.openlocfilehash: 7283ed099cefa4b0e137869724f8e87dda0d451a

---

# <a name="framework-libraries"></a>Bibliothèques de framework

.NET offre un grand ensemble standard de bibliothèques de classes, appelées bibliothèques de classes de base (ensemble principal) ou bibliothèques de classes de framework (ensemble complet). Ces bibliothèques fournissent des implémentations pour de nombreux types généraux et spécifiques d’une application, algorithmes et fonctionnalités d’utilitaire. Les bibliothèques commerciales et de la Communauté étant créées à partir des bibliothèques de classes de framework, elles sont tout de suite faciles à utiliser pour des tâches de calcul très diverses.

Une partie de ces bibliothèques est fournie avec chaque implémentation .NET. Les API de bibliothèque de classes de base doivent être incluses dans toutes les implémentations .NET parce que les développeurs le souhaitent et parce que les bibliothèques courantes en ont besoin pour s’exécuter. Les bibliothèques spécifiques aux applications en plus de la bibliothèque de classes de base, comme ASP.NET, ne sont pas disponibles dans toutes les implémentations .NET.

## <a name="base-class-libraries"></a>Bibliothèques de classes de base

Les bibliothèques de classes de base fournissent les types les plus fondamentaux ainsi que les fonctionnalités d’utilitaire et constituent la base de toutes les autres bibliothèques de classes .NET. Elles ont pour objectif de fournir des implémentations très générales sans préférer une charge de travail plutôt qu’une autre. Les performances sont toujours un facteur important, car les applications peuvent préférer une stratégie en particulier, comme la faible latence par rapport au haut débit ou une mémoire insuffisante par rapport à une faible utilisation du processeur. Ces bibliothèques sont généralement destinées à être très performantes et adoptent une approche intermédiaire en fonction des différents besoins en performances. Pour la plupart des applications, cette approche fonctionne plutôt bien.

## <a name="primitive-types"></a>Types primitifs

.NET inclut un ensemble de types primitifs qui sont utilisés (à des degrés divers) dans tous les programmes. Ces types contiennent des données, comme des nombres, des chaînes, des octets et des objets arbitraires. Le langage C# comprend des mots clés pour ces types. Un exemple d’ensemble de ces types est indiqué ci-dessous, avec les mots clés C# correspondants.

*   [System.Object](https://msdn.microsoft.com/library/system.object.aspx) ([object](https://msdn.microsoft.com/library/9kkx3h3c.aspx)) : Classe de base par excellence dans le système de type CRL. Elle constitue la racine de la hiérarchie des types.
*   [System.Int16](https://msdn.microsoft.com/library/system.int16.aspx) ([short](https://msdn.microsoft.com/library/ybs77ex4.aspx)) : Type entier signé 16 bits. L’entier non signé [UInt16](https://msdn.microsoft.com/library/system.uint16.aspx) existe également.
*   [System.Int32](https://msdn.microsoft.com/library/system.int32.aspx) ([int](https://msdn.microsoft.com/library/5kzh1b5w.aspx)) : Type entier signé 32 bits. L’entier non signé [UInt32](https://msdn.microsoft.com/library/x0sksh43.aspx) existe également.
*   [System.Single](https://msdn.microsoft.com/library/system.single.aspx) ([float](https://msdn.microsoft.com/library/b1e65aza.aspx)) : Type virgule flottante 32 bits.
*   [System.Decimal](https://msdn.microsoft.com/library/system.decimal.aspx) ([decimal](https://msdn.microsoft.com/library/364x0z75.aspx)) : Type décimal 128 bits.
*   [System.Byte](https://msdn.microsoft.com/library/system.byte.aspx) ([byte](https://msdn.microsoft.com/library/5bdb6693.aspx)) : entier non signé 8 bits qui représente un octet de mémoire.
*   [System.Boolean](https://msdn.microsoft.com/library/system.boolean.aspx) ([bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx)) : Type booléen qui représente « true » ou « false ».
*   [System.Char](https://msdn.microsoft.com/library/system.char.aspx) ([char](https://msdn.microsoft.com/library/x9h8tsay.aspx)) : Type numérique 16 bits qui représente un caractère Unicode.
*   [System.String](https://msdn.microsoft.com/library/system.string.aspx) ([string](https://msdn.microsoft.com/library/362314fe.aspx)) : Représente une série de caractères. Différent de `char[]`, mais permet l’indexation dans chaque `char` individuel de `string`.

## <a name="data-structures"></a>Structures de données

.NET inclut un ensemble de structures de données qui sont les bêtes de somme de presque toutes les applications .NET. Il s’agit essentiellement de collections, mais on retrouve également d’autres types.

*   [Array](https://msdn.microsoft.com/library/system.array.aspx) : Représente un tableau d’objets fortement typés accessibles par index. Sa taille est fixe, par sa construction.
*   [List](https://msdn.microsoft.com/library/6sh2ey19.aspx) : Représente une liste fortement typée d’objets accessibles par index. Est automatiquement redimensionnée en fonction des besoins.
*   [Dictionary](https://msdn.microsoft.com/library/xfhwa508.aspx) : Représente une collection de valeurs indexées par une clé. Les valeurs sont accessibles par une clé. Est automatiquement redimensionnée en fonction des besoins.
*   [Uri](https://msdn.microsoft.com/library/system.uri.aspx) : Fournit une représentation sous forme d’objet d’un URI (Uniform Resource Identifier) et un accès facile aux parties de l’URI.
*   [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx) : Représente un instant dans le temps, généralement exprimé sous la forme d’une date et d’une heure.

## <a name="utility-apis"></a>API d’utilitaire

.NET inclut un ensemble d’API d’utilitaire qui fournissent des fonctionnalités pour de nombreuses tâches importantes.

*   [HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient.aspx) : API qui permet d’envoyer des requêtes HTTP et de recevoir des réponses HTTP d’une ressource identifiée par un URI.
*   [XDocument](https://msdn.microsoft.com/library/system.xml.linq.xdocument.aspx) : API qui permet de charger et d’interroger des documents XML avec LINQ.
*   [StreamReader](https://msdn.microsoft.com/library/system.io.streamreader.aspx) : API qui permet de lire des fichiers ([StreamWriter](https://msdn.microsoft.com/library/system.io.stringwriter.aspx)). Peut être utilisée pour écrire des fichiers.

## <a name="appmodel-apis"></a>API de modèle d’application

Il existe de nombreux modèles d’application qui peuvent être utilisés avec .NET, fournis par plusieurs sociétés.

*   [ASP.NET](http://asp.net) : Fournit un framework web pour créer des sites et des services web. Pris en charge sur Windows, Linux et Mac OS (dépend de la version d’ASP.NET).



<!--HONumber=Nov16_HO1-->



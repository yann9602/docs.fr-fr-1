---
title: "Valeurs numériques dans .NET Core"
description: "Valeurs numériques dans .NET Core"
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6b8696be-55f5-4b66-98f3-69ff827c2c49
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 8e2aad830bdaccad6e8184fa462dd0d3157fd6c9
ms.lasthandoff: 03/13/2017

---

# <a name="numerics-in-net-core"></a>Valeurs numériques dans .NET Core

.NET Core prend en charge les primitives numériques standard pour les intégraux et les nombres à virgule flottante, ainsi que [System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger), un type intégral sans limite théorique supérieure ou inférieure, [System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex), un type qui représente des nombres complexes et un ensemble de types de vecteurs compatibles [SIMD](https://en.wikipedia.org/wiki/SIMD) (Single Instruction Multiple Data) de l’espace de noms [System.Numerics](https://docs.microsoft.com/dotnet/core/api/System.Numerics). 

## <a name="integral-types"></a>Types intégraux

Le .NET Core prend en charge les entiers signés et non signés, d’une longueur d’un à huit octets. Le tableau suivant répertorie les types intégraux et leur taille, indique s'ils sont signés ou non signés, et spécifie leur plage de valeurs. Tous les entiers sont des types valeur. 

Type | Signé/Non signé | Taille (en octets) | Valeur minimale | Valeur maximale
---- | --------------- | ------------ | ------------- | -------------
[System.Byte](https://docs.microsoft.com/dotnet/core/api/System.Byte) | Non signé | 1 | 0 | 255
[System.Int16](https://docs.microsoft.com/dotnet/core/api/System.Int16) | Signé | 2 | -32,768 | 32,767
[System.Int32](https://docs.microsoft.com/dotnet/core/api/System.Int32) | Signé | 4 | -2,147,483,648 | 2,147,483,647
[System.Int64](https://docs.microsoft.com/dotnet/core/api/System.Int64) | Signé | 8 | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807
[System.SByte](https://docs.microsoft.com/dotnet/core/api/System.SByte) | Signé | 1 | -128 | 127
[System.UInt16](https://docs.microsoft.com/dotnet/core/api/System.UInt16) | Non signé | 2 | 0 | 65,535
[System.UInt32](https://docs.microsoft.com/dotnet/core/api/System.UInt32) | Non signé | 4 | 0 | 4,294,967,295
[System.UInt64](https://docs.microsoft.com/dotnet/core/api/System.UInt64) | Non signé | 8 | 0 | 18 446 744 073 709 551 615

Chaque type intégral prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et de conversion implicite. Chaque entier comprend également des méthodes pour effectuer des comparaisons d'égalité et des comparaisons relatives, pour convertir la représentation sous forme de chaîne d'un nombre en cet entier et pour convertir un entier en sa représentation sous forme de chaîne. Certaines autres opérations mathématiques en dehors de celles qui sont gérées par les opérateurs standard, comme l’arrondi et l’identification de la valeur plus grande ou plus petite de deux entiers, sont disponibles à partir de la classe [System.Math](https://docs.microsoft.com/dotnet/core/api/System.Math). Vous pouvez également travailler avec les bits individuels d’une valeur entière à l’aide de la classe [System.BitConverter](https://docs.microsoft.com/dotnet/core/api/System.BitConverter). 
     
Notez que les types intégraux non signés ne sont pas conformes à CLS. Pour plus d’informations, consultez [Système de type commun et spécification CLS](common-type-system.md).

## <a name="floating-point-types"></a>Types virgule flottante

.NET Core comprend trois types à virgule flottante primitifs, qui sont répertoriés dans le tableau suivant. 

Type | Taille (en octets) | Valeur minimale | Valeur maximale
---- | ------------ | ------------- | -------------
[System.Double](https://docs.microsoft.com/dotnet/core/api/System.Double) | 8 | -1,79769313486232e308 | 1,79769313486232e308
[System.Single](https://docs.microsoft.com/dotnet/core/api/System.Single) | 4 | -3,402823e38 | 3,402823e38
[System.Decimal](https://docs.microsoft.com/dotnet/core/api/System.Decimal) | 16 | -79 228 162 514 264 337 593 543 950 335 | 79 228 162 514 264 337 593 543 950 335
   
Chaque type virgule flottante prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et de conversion implicite. Chacun comprend également des méthodes pour effectuer des comparaisons d'égalité et des comparaisons relatives, pour convertir la représentation sous forme de chaîne d'un nombre en virgule flottante et pour convertir un en nombre en virgule flottante en sa représentation sous forme de chaîne. Certaines autres opérations mathématiques, algébriques et trigonométriques sont disponibles à partir de la classe `Math`. Vous pouvez également travailler avec les bits individuels de valeurs `Double` et `Single` en utilisant la classe `BitConverter`. La structure `Decimal` a ses propres méthodes, `Decimal.GetBits` et `Decimal.Decimal(Int32())` pour travailler avec les bits individuel d'une valeur décimale, ainsi que son propre ensemble de méthodes pour effectuer d'autres opérations mathématiques. 

Les types `Double` et `Single` sont destinés à être utilisé pour des valeurs par nature imprécises (par exemple la distance entre deux étoiles dans le système solaire) et les applications dans lesquelles un haut degré de précision et une erreur d'arrondi réduite ne sont pas des impératifs. Vous devez utiliser le type `Decimal` pour les cas dans lesquels une plus grande précision est nécessaire et où les erreurs d’arrondi ne sont pas souhaitables.

## <a name="biginteger"></a>BigInteger

[System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger) est un type immuable qui représente un entier arbitrairement grand dont la valeur en théorie n’a pas de limite supérieure ou inférieure. Les méthodes du type `BigInteger` sont très proches de celles des autres types intégraux.  

## <a name="complex"></a>Complex

Le type [System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex) représente un nombre complexe, c’est-à-dire un nombre avec une partie réelle et une partie imaginaire. Il prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et de conversion implicite, ainsi que des méthodes mathématiques, algébriques et trigonométriques. 

## <a name="simd-enabled-vector-types"></a>Types de vecteurs compatibles SIMD

L’espace de noms `System.Numerics` comprend un ensemble de types de vecteurs compatibles SIMD pour .NET Core. SIMD permet à certaines opérations d’être parallélisées au niveau du matériel, ce qui se traduit par une nette amélioration des performances des applications mathématiques, scientifiques et graphiques qui effectuent des calculs sur les vecteurs. 

Les types de vecteurs compatibles SIMD rencontrés dans .NET Core sont les suivants : 

* Les types [System.Numerics.Vector2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector2), [System.Numerics.Vector3](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector3) et [System.Numerics.Vector4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector4), qui sont des vecteurs en 2, 3 et 4 dimensions de type `Single`.

* La structure [Vector&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector-1) qui vous permet de créer un vecteur de n’importe quel type numérique primitif. Les types numériques primitifs incluent tous les types numériques de l’espace de noms System à l’exception de Decimal.

* Deux types de matrices, [System.Numerics.Matrix3x2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix3x2), qui représentent une matrice 3 x 2, et [System.Numerics.Matrix4x4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix4x4), qui représente une matrice 4 x 4. 

* Le type [System.Numerics.Plane](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Plane), qui représente un plan en trois dimensions, et le type [System.Numerics.Quaternion](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Quaternion), qui représente un vecteur qui est utilisé pour encoder des rotations physiques en trois dimensions.


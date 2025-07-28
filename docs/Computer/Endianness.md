---
sidebar_position: 1
category: Computer
---

# Endianness (Boutisme)

C'est la manière dont un processeur lit les bits. 

## Big Endian (BE) - Grand boutisme
Les bits sont lu de **gauche** à **droite**:
- Le bit de poids fort et à **droite**.
- Le bit de poids faible et à **gauche**.

Exemple: `00010000` => `8`, `00010001` => `132`

## Little Endian (LE) - Petit boutisme
Les bits sont lu de **droite** à **gauche**:
- Le bit de poids fort et à **droite**.
- Le bit de poids faible et à **gauche**.

## 
Exemple: `00010000` => `16`, `00010001` => `17`
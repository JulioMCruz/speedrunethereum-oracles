# Oracles — notas de implementación

Este reto implementa tres modelos de oracle: una lista autorizada con mediana y filtro de datos obsoletos, nodos con staking y slashing por buckets, y un optimistic oracle con bonds, disputas y resolución por Decider.

## Verificación

- Pruebas locales: 81 aprobadas.
- Autograder de SpeedRunEthereum: 35 aprobadas; reto aceptado el 2026-09-13.
- Demo: https://speedrunethereum-oracles.vercel.app/optimistic
- OptimisticOracle verificado: https://sepolia.etherscan.io/address/0x84110f0901db94a28cb0664174b2d1710740c579#code
- Perfil: https://speedrunethereum.com/builders/0xc2564e41B7F5Cb66d2d99466450CfebcE9e8228f

## Contratos Sepolia

- WhitelistOracle: `0x01763c21642d41df7425622c025853c38f53c299`
- ORA: `0xbaa643a6457a9f4e586b0d9293330eda37d08163`
- StakingOracle: `0xa92ad5f6ef482e99699d70724fb875f32f540f69`
- OptimisticOracle: `0x84110f0901db94a28cb0664174b2d1710740c579`
- Decider: `0x7db464aebe183781dfcecfa4f1c0e8ddd7d732a2`

## Lecciones reutilizables

Los oráculos basados en whitelist priorizan velocidad y simplicidad, pero concentran confianza. El staking distribuye la participación y usa incentivos económicos, a cambio de más estado y operaciones. El modelo optimistic reduce el trabajo normal porque acepta propuestas no disputadas, pero añade latencia y convierte al mecanismo de resolución en una parte crítica de la seguridad.

En el flujo de publicación, la cuenta cifrada se descifra solo en memoria y se valida por dirección antes de desplegar. Vercel recibe la raíz del monorepo, usa `packages/nextjs` como Root Directory y construye con Yarn 4 mediante Corepack.

La nota técnica fue ingresada como conocimiento privado de `org_perkos` y vectorizada en PerkOS Knowledge con ID `kitem_d5b4fcfb246de42d`. Su validación independiente permanece pendiente.

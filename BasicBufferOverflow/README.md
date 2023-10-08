# Buffer Overflow Basico
Lembre-se, para gerar o binario vulneravél, é necessário desativar as proteções a nivel de compilador. Para isso, utilize os seguintes parametros:

gcc prog.c -o prog -z execstack -fno-stack-protector -no-pie -w

# Sobre a exploração
Como criamos um programa vulneravel, quando excedemos o limite de bytes esperado, acabamos sobrescrevendo outros espaços da memória, inclusive o endereço de retorno armazenado na stack e utilizado pela ret. Ou seja, podemos iniciar sobrescrever o endereço de retorno com um novo endereço de nosso interesse.

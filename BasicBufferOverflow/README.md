# Buffer Overflow Basico
Lembre-se, para gerar o binario vulneravél, é necessário desativar as proteções a nivel de compilador e desativar também o ASLR (Address space layout randomization). Para isso, utilize os seguintes parametros:

## Compilar o programa vulneravel
gcc prog.c -o prog -z execstack -fno-stack-protector -no-pie -w

## Desativar o ASLR
echo 0 | sudo tee /proc/sys/kernel/randomize_va_space

# Sobre a exploração
Como criamos um programa vulneravel, quando excedemos o limite de bytes esperado, acabamos sobrescrevendo outros espaços da memória, inclusive o endereço de retorno armazenado na stack e utilizado pela ret. Ou seja, podemos iniciar sobrescrever o endereço de retorno com um novo endereço de nosso interesse.

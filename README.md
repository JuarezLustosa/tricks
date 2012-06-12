tricks
======

Tricks for help development 

- Comando find em bash

  Comando para ajudar em alterações em vários arquivos
  
find app/models/ -name *.rb -exec sed -i '' 's/isso/vai_virar_isso/g' {} +
EX: find app/models/ -name *.rb -exec sed -i '' 's/#{unico\_db}\.//g' {} +
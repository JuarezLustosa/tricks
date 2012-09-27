tricks
======

Tricks for help development

`````
    Comando scp para copiar algo do servidor
````
    - scp -P NUMERO DA PORTA database@IPDAMAQUINA:/var/lib/postgresql/dump.tar.gz .

- Comando find em bash

  Comando para ajudar em alterações em vários arquivos
  
  - find app/models/ -name *.rb -exec sed -i '' 's/isso/vai_virar_isso/g' {} +
  - EX: find app/models/ -name *.rb -exec sed -i '' 's/#{unico\_db}\.//g' {} +

* Comando para renomear varios arquivos
  - for i in `find . -name '*.erb'` ; do mv $i ${i%erb}haml ; done 
  - By jonjon

- Comandos Gits
  Para remover comando indevido
  - git rebase --onto <rev> <rev> 


- Metaprograming

module Utils
  def output(message)
    puts message
  end
end

module MyApp extend Utils # OMG! This is totally new for me!
end

MyApp.output "hello"

- Avoid bundle exec

To avoid bundle exec use my gem rubygems-bundler it will automatically detect if Bundler.setup should be run.

Installation:

gem install rubygems-bundler
gem regenerate_binstubs # only once
The gem is already disributed with RVM so in most cases you should have it by default, just in case run once:

gem regenerate_binstubs # only once
You can find more information on the project page: https://github.com/mpapis/rubygems-bundler or on my blog: http://niczsoft.com/2012/05/rubygems-bundler-integration-gem-1-0-0/

- Rails Metodos 

Account.reflect_on_all_associations             # returns an array of all associations
Account.reflect_on_all_associations(:has_many)  # returns an array of all has_many associations
Source: show | on GitHub

reflect_on_all_autosave_associations()
Returns an array of AssociationReflection objects for all associations which have :autosave enabled.

reflect_on_association(association)
Returns the AssociationReflection object for the association (use the symbol).

Account.reflect_on_association(:owner)             # returns the owner AssociationReflection
Invoice.reflect_on_association(:line_items).macro  # returns :has_many

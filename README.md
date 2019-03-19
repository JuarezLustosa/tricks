tricks
======

Tricks for help development
```` 
Issue com Nokogiri 

Problema ao tentar instalar a gem Nokogiri e encontrar o seguinte erro

libxml2 is missing.  please visit http://nokogiri.org/tutorials/installing_nokogiri.html for help with installing dependencies.

gem install nokogiri -v 1.5.0 -- --use-system-libraries=true --with-xml2-include=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.9.sdk/usr/include/libxml2

Relembrar de verificar o paht do include, a versão do sdk pode estar diferente
````

`````
    Comando scp para copiar algo do servidor
    
    - scp -P NUMERO DA PORTA database@IPDAMAQUINA:/var/lib/postgresql/dump.tar.gz .
````

````
    Ruby Rails 
    
    para pesqiosa subquerys
    x = Price.select("*").from("(#{sql}) as subquery")
    puts x.first.avg_price


`````
    Adicionar porta no iptables
    
    iptables -A INPUT -m multiport -p tcp --dport 5432 -j ACCEPT
````

`````
    Resolvendo o seguinte erro 
    
    "RuntimeError ( Ghostscript not found in your environment.
    Install it and set the variable RGhost::Config::GS[:path] with the executable.
    Example: RGhost::Config::GS[:path]='/path/to/my/gs' #unix-style
    RGhost::Config::GS[:path]="C:\\gs\\bin\\gswin32c.exe"  #windows-style
    ):"
    
    
     - sudo mkdir -p /opt/local/bin/
     - sudo ln -s /usr/local/bin/gs /opt/local/bin/gs
````

`````
    Comando postgres para dar acesso a um usuário a todas as tabelas de um banco
    
    - psql -U postgres -qAt -c "select 'grant select on ' || tablename || ' to \"user\";' from pg_tables where schemaname = 'public'" nome_do_banco | psql -U postgres nome_do_banco
````

- Comando find em bash

  Comando para ajudar em alterações em vários arquivos
  
  - find app/models/ -name *.rb -exec sed -i '' 's/isso/vai_virar_isso/g' {} +
  - EX: find app/models/ -name *.rb -exec sed -i '' 's/#{unico\_db}\.//g' {} +

* Comando para renomear varios arquivos
  - for i in `find . -name '*.erb'` ; do mv $i ${i%erb}haml ; done 
  - By jonjon

* Comando para matar varios processos de uma vez atraves do grep
  - kill -9 `ps aux | grep 20121126165651 | grep -v grep | awk '{print $2}'`
 

- Comandos Gits
  Para remover comando indevido
  - git rebase --onto <rev> <rev> 


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


----- Para invocar uma rake dentro de outra rake -----

task :invoke_another_task do
  # some code
  Rake::Task["another:task"].invoke
end


------- GIT ----------

http://nvie.com/posts/a-successful-git-branching-model/

https://nathanhoad.net/deploy-from-a-git-tag-with-capistrano

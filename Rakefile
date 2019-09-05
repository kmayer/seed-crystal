require "erb"

ViewData = Struct.new(:brewfile, :vsc_extensions)

task :default => :test

file "seed-workstation.sh" => [__FILE__, "seed-workstation.sh.erb"] do
  view_data = ViewData.new
  view_data.brewfile = File.read("Brewfile")
  view_data.vsc_extensions = %w[
    aaron-bond.better-comments
    bajdzis.vscode-database
    bung87.rails
    bung87.vscode-gemfile
    castwide.solargraph
    christian-kohler.npm-intellisense
    CoenraadS.bracket-pair-colorizer-2
    donjayamanne.githistory
    earshinov.permute-lines
    eg2.vscode-npm-script
    esbenp.prettier-vscode
    formulahendry.auto-rename-tag
    gurgeous.bust-a-gem
    jpoissonnier.vscode-styled-components
    juanartero.ruby-markers
    kumar-harsh.graphql-for-vscode
    leighlondon.eml
    matthieumu.vscode-rubycommentdoc
    mgmcdermott.vscode-language-babel
    mikestead.dotenv
    ms-azuretools.vscode-docker
    ms-vsliveshare.vsliveshare
    noku.rails-run-spec-vscode
    pkosta2005.heroku-command
    rebornix.ruby
    Shan.code-settings-sync
    sianglim.slim
    sporto.rails-go-to-spec
    sysoev.language-stylus
    waderyan.gitblame
    xabikos.ReactSnippets
  ]
  erb = ERB.new(File.read("seed-workstation.sh.erb"))
  File.open("seed-workstation.sh", "w") { |f| f.write erb.result(binding) }
end

task :test => "seed-workstation.sh" do
  sh "shellcheck seed-workstation.sh -e SC2039"
end
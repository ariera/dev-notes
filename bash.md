```
alias t="cd /var/www/ticketing/current"
alias migrate="RAILS_ENV=production bundle exec rake db:migrate"
alias rc="RAILS_ENV=production bundle exec rails c"
alias redrop="RAILS_ENV=production bundle exec rake db:drop; RAILS_ENV=production bundle exec rake db:create; RAILS_ENV=production bundle exec rake db:migrate"
alias assets="RAILS_ENV=production bundle exec rake assets:precompile"
alias restart_nginx="sudo service nginx restart"

function finish_deploy {
  pushd /var/www/ticketing/current
  migrate
  assets
  restart_resque
  restart_nginx
  popd
}

function kill_resque {
  ps axf | grep resque | grep -v grep | awk '{print "kill -9 " $1}' | sh
}

function launch_resque {
  pushd /var/www/ticketing/current
  RAILS_ENV=production QUEUE=* bundle exec rake resque:work &
  popd
}

function restart_resque {
  kill_resque
  launch_resque
}
```

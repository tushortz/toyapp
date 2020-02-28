# frozen_string_literal: true

# A sample Guardfile
# More info at https://github.com/guard/guard#readme

# Uncomment and set this to only include directories you want to watch
directories %w[app lib config test spec features].select { |d|
  Dir.exist?(d) ? d : UI.warning("Directory #{d} does not exist")
}

## Note: if you are using the `directories` clause above and you are not
## watching the project directory ('.'), then you will want to move
## the Guardfile to a watched dir and symlink it back, e.g.
#
#  $ mkdir config
#  $ mv Guardfile config/
#  $ ln -s config/Guardfile .
#
# and, you'll have to watch "config/Guardfile" instead of "Guardfile"
guard :minitest, spring: '/bin/rails test', all_on_start: false do
  watch(%r{^test/(.*)/?(.*)_test\.rb$})
  watch('test/test_helper.rb') { 'test' }
  watch('config/routes.rb') { interface_tests }
  watch(%r{^app/views/layouts/*}) { interface_tests }
  watch(%r{^app/models/(.*)\.rb$}) do |matches|
    "test/models/#{ matches[1] }_test.rb"
  end
end

namespace :book do
  desc 'build basic book formats'
  task :build do

    begin
      output_dir = './build'
      book_name = 'book-template'
      book_file = "book/#{book_name}.adoc"
      version_string = ENV['TRAVIS_TAG'] || `git describe --tags`.chomp
      if version_string.empty?
        version_string = '0'
      end
      date_string = Time.now.strftime("%Y-%m-%d")
      params = "--attribute revnumber='#{version_string}' --attribute revdate='#{date_string}'"

      puts "Converting to HTML..."
      `bundle exec asciidoctor #{params} -D #{output_dir} -a data-uri #{book_file}`
      puts " -- HTML output at #{output_dir}/#{book_name}.html"

      puts "Converting to EPub..."
      `bundle exec asciidoctor-epub3 #{params} -D #{output_dir} #{book_file}`
      puts " -- Epub output at #{output_dir}/#{book_name}.epub"

      puts "Converting to PDF... (this one takes a while)"
      `bundle exec asciidoctor-pdf #{params} -a index -D #{output_dir} #{book_file} 2>/dev/null`
      puts " -- PDF output at #{output_dir}/#{book_name}.pdf"

    end
  end
end

task :default => "book:build"

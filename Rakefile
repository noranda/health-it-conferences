require 'yaml'

def slugify(tag)
  tag.downcase.gsub(/\s+/, '-')
end

namespace :tags do
  desc 'Generates the markdown tag files'
  task :generate do
    tags = []
    base_dir = File.dirname(__FILE__)
    Dir.glob("#{base_dir}/_posts/*.md").each do |post|
      contents = File.read(post)
      yaml_content = contents.split(/---/, 3)[1]

      post_config = YAML.load(yaml_content)
      post_config['tags'].each do |tag|
        tags << tag unless tags.include?(tag)
      end
    end

    tags.sort!

    tags_data = tags.map do |tag|
      { 'slug' => slugify(tag), 'name' => tag }
    end

    puts "Writing _data/tags.yml"
    File.open("#{base_dir}/_data/tags.yml", 'w') { |f| f.write(YAML.dump(tags_data)) }

    Dir.glob("#{base_dir}/conferences/tag/*.md").each do |file|
      puts "Removing file: #{file}"
      File.unlink(file)
    end

    tags_data.each do |tag_data|
      puts "Writing conferences/tag/#{tag_data['slug']}.md"

      File.open("#{base_dir}/conferences/tag/#{tag_data['slug']}.md", 'w') do |f|
        f.write(YAML.dump({
          'layout' => 'conference_by_tag',
          'tag' => tag_data['name'],
          'permalink' => "conferences/tag/#{tag_data['slug']}/"
        }))
        f.write('---')
      end
    end
  end
end
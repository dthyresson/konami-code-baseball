require 'awesome_print'
require 'oj'
require 'yaml'

task :default do
  puts 'Batter up!'

  Rake::FileList['data/pitches/*.json'].each do |filename|
    file_slug = File.basename(filename, '.json').gsub('-', '_')

    pitch_json = Oj.load_file(filename)

    konami_code_pitch_counts = pitch_json.dig('konami_code_pitch_counts') || []
    pitches = pitch_json.dig('pitches') || []
    pitch_stylesheet = "#{file_slug}_presses"

    File.open("source/assets/stylesheets/pitches/#{pitch_stylesheet}.css.scss", 'w') do |f|
      File.open("source/pitches/#{file_slug}.html.erb", 'w') do |w|
        w.puts YAML.dump(pitch_json)
        w.puts "---\n"
        w.puts "<%= stylesheet_link_tag 'pitches/#{pitch_stylesheet}' %>"
      end

      f.puts "@import 'presses';"
      f.puts "@import 'gamepad';"
      f.puts "svg#gamepad { .pad-button { animation-duration: #{pitches.count / 2}s } }";

      ['U', 'D', 'R', 'L', 'A', 'B'].each do |button|
        f << write_button_animation(pitches: pitches,
                                    konami_code_pitch_counts: konami_code_pitch_counts,
                                    pitch_kode: button)
      end

    end
  end
end

def write_button_animation(pitches: [],
                          konami_code_pitch_counts: [],
                          pitch_kode: '')
  css = ''
  pitch_count = pitches.count
  frame_interval = 100.000 / (pitch_count * 2)

  css += "@keyframes #{pitch_kode.downcase}-button-presses {"

  css += "0% { opacity: $off };"

  f = 0
  pitches.each_with_index do |pitch, i|
    f += frame_interval
    if konami_code_pitch_counts.include?((pitch['pitch_count'].to_i - 1)) && pitch.dig('pitch_kode') == pitch_kode
      css += "#{f}% { opacity: $on };"
      f += frame_interval
      css += "#{f}% { opacity: $off };"
    elsif pitch.dig('pitch_kode') == pitch_kode
      css += "#{f}% { opacity: $touch };"
      f += frame_interval
      css += "#{f}% { opacity: $off };"
    elsif pitch.dig('pitch_kode') == '' && pitch_kode == 'A'
      css += "#{f}% { opacity: $touch };"
      f += frame_interval
      css += "#{f}% { opacity: $off };"
    elsif pitch.dig('pitch_outcome_type')[0] == 'k' && pitch_kode == 'B'
      css += "#{f}% { opacity: $touch };"
      f += frame_interval
      css += "#{f}% { opacity: $off };"
    else
      css += "#{f}% { opacity: $off };"
      f += frame_interval
      css += "#{f}% { opacity: $off };"
    end
  end
  css += "100% { opacity: $off };"
  css += "}"
end

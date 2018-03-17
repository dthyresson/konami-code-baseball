require 'awesome_print'
require 'oj'


task :default do
  puts 'Batter up!'


  #load pitch json

  json = Oj.load_file('json/pitches-mlb-2017-cle-min-2017-08-17-1210-mlb-kyle-gibson.json')

  konami_code_pitch_counts = json.dig('konami_code_pitch_counts') || []
  pitches = json.dig('pitches') || []

  # ap pitch_count

  ap konami_code_pitch_counts

  ['U', 'D', 'R', 'L', 'A', 'B'].each do |button|
    make_button_animation(pitches: pitches, konami_code_pitch_counts: konami_code_pitch_counts, pitch_kode: button)
  end
end

def make_button_animation(pitches: [], konami_code_pitch_counts: [], pitch_kode: '')
  pitch_count = pitches.count
  frame_interval = 100.000 / (pitch_count * 2)

  puts "@keyframes #{pitch_kode.downcase}-button-presses {"

  puts "0% { opacity: $off };"

  f = 0
  pitches.each_with_index do |pitch, i|
    f += frame_interval
    if konami_code_pitch_counts.include?((pitch['pitch_count'].to_i - 1)) && pitch.dig('pitch_kode') == pitch_kode
      puts "#{f}% { opacity: $on };"
      f += frame_interval
      puts "#{f}% { opacity: $off };"
    elsif pitch.dig('pitch_kode') == pitch_kode
      puts "#{f}% { opacity: $touch };"
      f += frame_interval
      puts "#{f}% { opacity: $off };"
    elsif pitch.dig('pitch_kode') == '' && pitch_kode == 'A'
      puts "#{f}% { opacity: $touch };"
      f += frame_interval
      puts "#{f}% { opacity: $off };"
    elsif pitch.dig('pitch_outcome_type')[0] == 'k' && pitch_kode == 'B'
      puts "#{f}% { opacity: $touch };"
      f += frame_interval
      puts "#{f}% { opacity: $off };"
    else
      puts "#{f}% { opacity: $off };"
      f += frame_interval
      puts "#{f}% { opacity: $off };"
    end
  end
  puts "100% { opacity: $off };"
  puts "}"
end

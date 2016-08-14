namespace :pki do
  desc "Pull keys and certs from ca, CA=[../ca]"
  task :pull do
    ca = ENV['CA'] || File.join(__dir__, "../ca")
    outbox = File.expand_path(File.join(ca, 'out'))
    unless Dir.exist?(outbox)
      fail "Expected directory to exist: #{outbox}"
    end
    puts "Using keys in #{outbox}"

    dsts = Dir.glob("./**/files/**/*.{crt,key}")
    cps = dsts.map do |dst|
      src = File.join(outbox, File.basename(dst))
      if ! File.exist?(src)
        fail "Expected source file to exist: #{src}"
      end

      head = File.read(src, 512)
      unless head.match(/--BEGIN.*(PRIVATE KEY|CERTIFICATE)--/)
        fail "Not a cert or private key (locked?): #{src}"
      end
	    [src, dst]
	  end.to_h

    cps.each do |src, dst|
      cp src, dst
    end
  end
end

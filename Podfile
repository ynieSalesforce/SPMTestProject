# Uncomment the next line to define a global platform for your project
platform :ios, '15.0'
source 'https://cdn.cocoapods.org/'

use_frameworks!

target 'SPMTestProject' do
  pod 'SQLite.swift/SQLCipher', '~> 0.13.3'
  pod 'Shimmer', '~> 1.0'
  pod "Updates", :git => 'https://github.com/rwbutler/Updates.git', :tag => '1.6.1'
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '15.0'
      config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
      config.build_settings["ARCHS"] = "$(ARCHS_STANDARD)"
    end
    if target.respond_to?(:product_type) and target.product_type == "com.apple.product-type.bundle"
      target.build_configurations.each do |config|
        config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      end
    end
  end
end

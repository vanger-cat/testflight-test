# Rakefile
include Rake::DSL
require 'bundler'
Bundler.require

Wox::Tasks.create :info_plist => 'testflightenterprise/testflightenterprise-Info.plist', :sdk => 'iphoneos', :configuration => 'Release' do
  build :debug, :configuration => 'Debug'

  build :release, :developer_certificate => 'iPhone Distribution: Flexis ZAO' do
    ipa :app_store, :provisioning_profile => 'App Store'
    ipa :adhoc, :provisioning_profile => '2BE7349A-262D-406B-8EEE-E2F3A8C9D1F0' do
      testflight :publish, :api_token => 'af7140355be791bf7248083aab49f055_MTQzNzk0MjAxMS0wOC0zMSAwNjowMDoyMi40MzIzNjI',
                           :team_token => '72d93b9ce388656e3e34638ff95b86a4_NjIzMDIyMDEyLTAzLTA5IDA5OjUxOjE4LjA2ODQwMQ',
                           :notes => proc { File.read("CHANGELOG") },
                           :distribution_lists => %w[All],
                           :notify => true

    end
  end
end
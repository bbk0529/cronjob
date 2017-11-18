
namespace :telegram do
	task :hello do
		puts "hellooooo"

	end
end


namespace :db do
	task :migrate do
		puts "rake db migrate"
	end
end


namespace :telegram do
	task :sendmsg do
		require 'rest-client'
		require 'nokogiri'
		require 'awesome_print'
		require 'json'

		token=ENV['TELEGRAM_TOKEN']
		telegram_uri = "https://api.telegram.org/bot"
		talk=JSON.parse(RestClient.get(telegram_uri + "#{token}" + "/getUpdates"))

		chat_id=talk['result'][0]['message']['chat']['id']

	   	uri = "https://search.naver.com/search.naver?sm=tab_hty.top&where=nexearch&query=%ED%99%98%EC%9C%A8&oquery=%EC%9C%A0%EA%B0%80&tqi=TlGGiwpySEKssc9YZ24ssssssKR-204396"
	   	response = RestClient.get(uri)
	   	text = Nokogiri::HTML(response.body)
	  	component=text.css('.rate_table_bx').text


		message = "[#{Time.now()}]" +  component
		url = (telegram_uri + "#{token}" +  "/sendmessage?chat_id=#{chat_id}&text=#{message}")
		RestClient.get(URI.encode(url))
	end
end

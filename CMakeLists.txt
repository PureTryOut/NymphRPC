cmake_minimum_required(VERSION 3.10)

project(
	nymphrpc
	VERSION 0.1
	LANGUAGES CXX
)

find_package(Poco COMPONENTS Foundation Net JSON REQUIRED CONFIG)

add_subdirectory(src)

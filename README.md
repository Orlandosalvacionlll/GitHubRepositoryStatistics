# GitHubRepositoryStatistics

import requests

def get_github_stats(username, repository):
    # GitHub API endpoint for repository statistics
    api_url = f'https://api.github.com/repos/{username}/{repository}'

    # Make a GET request to the GitHub API
    response = requests.get(api_url)

    # Check if the request was successful (status code 200)
    if response.status_code == 200:
        # Parse the JSON response
        repo_data = response.json()

        # Extract relevant information
        stars = repo_data['stargazers_count']
        forks = repo_data['forks']
        issues = repo_data['open_issues']

        # Return the statistics
        return {
            'Stars': stars,
            'Forks': forks,
            'Open Issues': issues
        }
    else:
        # Print an error message if the request was not successful
        print(f"Error: Unable to fetch repository data. Status code: {response.status_code}")
        return None

def main():
    # GitHub username and repository name
    username = 'your_username'
    repository = 'your_repository'

    # Get GitHub statistics for the specified repository
    stats = get_github_stats(username, repository)

    # Print the statistics
    if stats:
        print(f"GitHub Repository Statistics for {username}/{repository}:")
        for key, value in stats.items():
            print(f"{key}: {value}")

if __name__ == "__main__":
    main()
